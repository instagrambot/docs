# Documentation for Developers

This is documentation for developers, where we provide our bot methods as an API for your needs. Instagram API [deprecated](https://www.instagram.com/developer/changelog/) practically all of their methods, so we use their mobile API. We are hiding under the mask of mobile phone. Instagram servers think that your requests from instabot are made from some mobile app. By the way we got some cases of ban by them, our mask is not perfect. We are hardly trying to make your requests as safe as they could be. For example, we restricted the amount of likers of some picture til 999.

By the way we hardly recommend you not to use your own account if you don't need your personal data or don't want to promote your account.

## Quickstart

For the better understanding of how bot works, let's start with a quick example:

``` python
from instabot import Bot


bot = Bot()
bot.login(username="YOUR_LOGIN", password="YOUR_PASSWORD")
user_id = bot.get_user_id_from_username("lego")
user_info = bot.get_user_info(user_id)
print(user_info['biography'])
```

The output of program would be greeting phrase from [official LEGO account](https://www.instagram.com/lego/?hl=ru). At the time of writing documentation we got this:
```
Hello! You made it to the official #LEGO Instagram - where everything is awesome!
```

## Bot Parameters

**proxy** — Proxy for Instabot. Default: `None`. Example: `TODO`

**max_likes_per_day** — How many likes the bot will perform per day. Default: 1000

**max_unlikes_per_day** — How many medias the bot will unlike in a day. Default: 1000

**max_follows_per_day** — Max number of follow per day. Default: 350

**max_unfollows_per_day** — Max number of unfollow per day. Default: 350

**max_comments_per_day** — Max number of comments per day. Default: 100

**max_likes_to_like** — If the media has more likes then this value — it will be ignored and not be liked. Default: 200

**filter_users** — Filter users if True. Default: True

**filter_business_accounts** — Filter business accounts if True. Default: True

**filter_verified_accounts** — Filter verified accounts if True. Default: True

**max_followers_to_follow** — If the user has more followers than this value — the user will not be followed or liked. Default: 2000

**min_followers_to_follow** — If the user has fewer followers than this value — the user will not be followed or liked. Default: 10

**max_following_to_follow** — If the user has more followings than this value — the user will not be followed or liked. Default: 10000

**min_following_to_follow** — If the user has fewer followings than this value — the user will not be followed or liked. Default: 10

**max_followers_to_following_ratio** — if the user's followers/following is greater than this value — the user will not be followed or liked. Default: 10

**max_following_to_followers_ratio** — if user's following/followers is greater than this value — he will not be followed or liked. Default: 2

**min_media_count_to_follow** — If the user has fewer media count than this value — the user will not be followed. Default: 3

**max_following_to_block** — If the user have a following more than this value — the user will be blocked in blocking scripts because he is a massfollower. Default: 2000

**max_likes_to_like** — Max number of likes that can media have to be liked. Default: 100 

**like_delay** — Delay between likes in seconds. Default: 10

**unlike_delay** — Delay between unlikes in seconds. Default: 10

**follow_delay** — Delay between follows in seconds. Default: 30

**unfollow_delay** — Delay between unfollows in seconds. Default: 30

**comment_delay** — Delay between comments in seconds. Default: 60

**whitelist** — Path to the file with users that shouldn't be unfollowed. Default: `whitelist.txt`

**blacklist** — Path to the file with users that shouldn't be followed, liked or commented. Default: `blacklist.txt`

**comments_file** — Path to the comments database . Default: `comments.txt`

**stop_words** — A list of stop words: don't follow a user if they have any of these stop words in their description. Default: ['shop', 'store', 'free']

In all files there are one item per line. So, file:
``` python
Nice!
Great!
Good pic!
```
You should read as `["Nice!", "Great!", "Good pic!"]`

# Bot Methods

Methods of `Bot` instance, that you could use as API calls.

### Auth

**login** — Method that authenticates you in Instagram.

Args:

- _login_, _password_ — you could pass login and password and bot would use them. Bot would ask you for them by default.
- _force_ — forses bot to re-login. False by default.
- _proxy_ — proxy server that bot would use during authentication 
- *use_cookie* — means that bot would use cookies not to re-login every time it needs to push some request. Defaults as True.
- *cookie_fname* — filename where cookies would be stored. Default value: `cookie.txt`.

**logout** — Loggs you out.

### Get

<a name="get_your_medias"></a> **get_your_medias** — Get list of ids of your last medias.

Args:

- _as_dict_ — With parameter as_dict=True returns media as dict. False by default.

Example: `bot.get_you_medias()`
Answer: `[1900986973457183396, 1900986921481250054]`

<a name="get_timeline_medias"></a> **get_timeline_medias** — Get list of media_ids from your timeline feed

Example: `bot.get_timeline_medias()`
Answer: `[1900986973457183396, 1900986921481250054]`

<a name="get_user_medias"></a> **get_user_medias** — Get list of 20 last user's medias.

Args:

- *user_id* — Id of user that you want to fetch. See [get_user_id_from_username](TODO)
- *filtration* — Bot would filter those publications, witch are not satisfies bot parameters as `max_likes_to_like` and `min_likes_to_like`. All medias between them would be displayed. Defaults as True.
- *is_comment* — Filtration of medias that has/hasn't a comment.

Example: `bot.get_user_medias("lego")`
Answer: `[1900986973457183396, 1900986921481250054]`

<a name="get_total_user_medias"></a> **get_total_user_medias** — Same as [get_user_medias](#get_user_medias), but fetches all of user's medias.

Args:

- *user_id* — Id of user that you want to fetch. See [get_user_id_from_username](TODO)

<a name="get_hashtag_medias"></a> **get_hashtag_medias** — Get list of medias by hashtag.

Example: `bot.get_hashtag_medias("cats")`
Answer: `[1900986973457183396, 1900986921481250054]`

**get_geotag_medias** — Get list of medias by geotag

Example: `TODO`

**get_timeline_users** — Get list of users from your timeline feed

Example: `bot.get_timeline_users()`

**get_hashtag_users** — Get list of users who posted with hashtag

Example: `bot.get_hashtag_users("Dog")`

**get_geotag_users** — Get list of users who posted with geotag

Example: `TODO`

**get_userid_from_username** — Convert username to user_id

Example: `bot.get_userid_from_username("ohld")`

**get_user_followers** — Get list of user's followers

Example: `bot.get_user_followers("competitor")`

**get_user_following** — Get list of user's following

Example: `bot.get_user_following("competitor")`

**get_media_likers** — Get list of media likers

Example: `bot.get_media_likers("12312412")`

**get_media_comments** — Get list of media's comments

Example: `bot.get_media_comments("12312412")`

**get_comment** — Get comment from comment file

Example: `bot.get_comment()`

**get_media_commenters** — Get list of users who commented on the media

Example: `bot.get_media_commenters("12321")`

### Like

**like** — Like media_id.

Example: `bot.like("1231241210")`

**like_medias** — Like medias from list.

Example: `bot.like_medias(["1323124", "123141245"])`

**like_timeline** — Like medias from your timeline feed

Example: `bot.like_timeline()`

**like_user** — Like last user's medias

Example: `bot.like_user("activefollower")`

**like_hashtag** — Like last medias with hashtag.

Example: `bot.like_hashtag("dog")`

**like_geotag** — Like last medias with geotag

Example: `TODO`

### Unlike

**unlike** — Remove like from media.

Example: `bot.unlike("12321412512")`

**unlike_medias** — Remove likes from medias in list

Example: `bot.unlike_medias(["123", "321"])`

### Follow

**follow** — Follow user.

Example: `bot.follow("activefollower")`

**follow_users** — Follow users from list.

Example: `bot.follow(["activefollower1", "activefollower2"])`

### Unfollow

**unfollow** — Unfollow user.

Example: `bot.unfollow("competitor")`

**unfollow_users** — Unfollow users from list.

Example: `bot.unfollow_users(["competitor1", "competitor2"])`

**unfollow_non_followers** — Unfollow users who don't follow you.

Example: `bot.unfollow_non_followers()`

### Comment

**comment** — Put a comment under the media.

Example: `bot.comment("1231234", "Nice pic!")`

**comment_medias** — Put comments under medias from list.

Example: `bot.comment_medias(["123", "321"])`

**comment_hashtag** — Put comments under medias by hashtag

Example: `bot.comment_hashtag("Dog")`

**comment_geotag** — Put comments under medias by geotag.

Example: `TODO`

**comment_users** — Put comments under users' last medias.

Example: `bot.comment_users(["activefollower1", "activefollower2"])`

**is_commented** — Check if media is already commented.

Example: `bot.is_commented("123321")`

### Photos

**upload_photo** — Uploads photo to your account.

Example: `bot.upload_photo("/somephoto.jpg", caption="Nice pic!")`

**download_photo** — Downloads photo by id.

Example: `bot.download_photo(["123", filename="somefile.jpg")`

**download_photos** — Downloads photos by ids into given folder.

Example: `bot.download_photos(["123","345"], "photos")|`
