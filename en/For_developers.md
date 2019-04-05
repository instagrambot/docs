# <a name="Intro"></a> Documentation for Developers

This is documentation for developers, where we provide our bot methods as an API for your needs. Instagram API [deprecated](https://www.instagram.com/developer/changelog/) practically all of their methods, so we use their mobile API. We are hiding under the mask of mobile phone. Instagram servers think that your requests from instabot are made from some mobile app. By the way we got some cases of ban by them, our mask is not perfect. We are hardly trying to make your requests as safe as they could be. For example, we restricted the amount of likers of some picture til 999.

By the way we hardly recommend you not to use your own account if you don't need your personal data or don't want to promote your account.

# <a name="Contents"></a> Contents

- [Intro](#Intro)
- [Contents](#Contents)
- [Quickstart](#Quickstart)
- [Bot parameters](#Params)
- [Bot Methods](#Methods)
  + [Auth](#Auth)
    + [login](#login)
    + [logout](#logout)
  + [IDs](#ids)
    + [get_user_id_from_username](#get_user_id_from_username)
    + [get_username_from_user_id](#get_username_from_user_id)
    + [get_media_id_from_link](#get_media_id_from_link)
    + [get_link_from_media_id](#get_link_from_media_id)
  + [Get medias](#getmedias)
    + [get_user_medias](#get_user_medias)
    + [get_your_medias](#get_your_medias)
    + [get_timeline_medias](#get_timeline_medias)
    + [get_total_user_medias](#get_total_user_medias)
    + [get_hashtag_medias](#get_hashtag_medias)
    + [get_geotag_medias](#get_geotag_medias)
  + [Get users](#getusers)
    + [get_timeline_users](#get_timeline_users)
    + [get_hashtag_users](#get_hashtag_users)
    + [get_geotag_users](#get_geotag_users)
    + [get_user_followers](#get_user_followers)
    + [get_user_following](#get_user_following)
    + [get_media_likers](#get_media_likers)
    + [get_media_commenters](#get_media_commenters)
  + [Comments](#comments)
    + [get_media_comments](#get_media_comments)
    + [get_media_comments_all](#get_media_comments_all)
    + [get_comment](#get_comment)
    + [comment](#comment)
    + [comment_medias](#comment_medias)
    + [comment_hashtag](#comment_hashtag)
    + [comment_geotag](#comment_geotag)
    + [comment_users](#comment_users)
    + [is_commented](#is_commented)
  + [Likes](#likes)
    + [like](#like)
    + [like_medias](#like_medias)
    + [unlike](#unlike)
    + [unlike_medias](#unlike_medias)
    + [like_timeline](#like_timeline)
    + [like_user](#like_user)
    + [like_hashtag](#like_hashtag)
    + [like_geotag](#like_geotag)
  + [Follows](#follows)
    + [follow](#follow)
    + [follow_users](#follow_users)
    + [unfollow](#unfollow)
    + [unfollow_users](#unfollow_users)
    + [unfollow_non_followers](#unfollow_non_followers)
  + [Photos](#photos)
    + [upload_photo](#upload_photo)
    + [download_photo](#download_photo)
    + [download_photos](#download_photos)
  
## <a name="Quickstart"></a> Quickstart

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

##  <a name="Params"></a> Bot Parameters

**proxy** — Proxy for Instabot.

Default: `None`.

Example: `TODO`

**max_likes_per_day** — How many likes the bot will perform per day.

Default: 1000

**max_unlikes_per_day** — How many medias the bot will unlike in a day.

Default: 1000

**max_follows_per_day** — Max number of follow per day.

Default: 350

**max_unfollows_per_day** — Max number of unfollow per day.

Default: 350

**max_comments_per_day** — Max number of comments per day.

Default: 100

**max_likes_to_like** — If the media has more likes then this value — it will be ignored and not be liked.

Default: 200

**filter_users** — Filter users if True.

Default: True

**filter_business_accounts** — Filter business accounts if True.

Default: True

**filter_verified_accounts** — Filter verified accounts if True.

Default: True

**max_followers_to_follow** — If the user has more followers than this value — the user will not be followed or liked. 

Default: 2000

**min_followers_to_follow** — If the user has fewer followers than this value — the user will not be followed or liked. 

Default: 10

**max_following_to_follow** — If the user has more followings than this value — the user will not be followed or liked. 

Default: 10000

**min_following_to_follow** — If the user has fewer followings than this value — the user will not be followed or liked. 

Default: 10

**max_followers_to_following_ratio** — if the user's followers/following is greater than this value — the user will not be followed or liked.

Default: 10

**max_following_to_followers_ratio** — if user's following/followers is greater than this value — he will not be followed or liked.

Default: 2

**min_media_count_to_follow** — If the user has fewer media count than this value — the user will not be followed.

Default: 3

**max_following_to_block** — If the user have a following more than this value — the user will be blocked in blocking scripts because he is a massfollower.

Default: 2000

**max_likes_to_like** — Max number of likes that can media have to be liked.

Default: 100 

**like_delay** — Delay between likes in seconds.

Default: 10

**unlike_delay** — Delay between unlikes in seconds.

Default: 10

**follow_delay** — Delay between follows in seconds.

Default: 30

**unfollow_delay** — Delay between unfollows in seconds.

Default: 30

**comment_delay** — Delay between comments in seconds.

Default: 60

**whitelist** — Path to the file with users that shouldn't be unfollowed.

Default: `whitelist.txt`

**blacklist** — Path to the file with users that shouldn't be followed, liked or commented.

Default: `blacklist.txt`

**comments_file** — Path to the comments database.

Default: `comments.txt`

**base_path** — Base directory path for local files such as comments_file, blacklist, whitelist, etc..

Default: `./`

**stop_words** — A list of stop words: don't follow a user if they have any of these stop words in their description. 

Default: ['shop', 'store', 'free']

---

In all files there are one item per line. So, file:
``` python
Nice!
Great!
Good pic!
```
You should read as `["Nice!", "Great!", "Good pic!"]`

# <a name="Methods"></a> Bot Methods

Methods of `Bot` instance, that you could use as API calls.

### <a name="Auth"></a> Auth

<a name="login"></a> **login** — Method that authenticates you in Instagram.

Parameters:

- _login_, _password_ — you could pass login and password and bot would use them. Bot would ask you for them by default.
- _force_ — forses bot to re-login. False by default.
- _proxy_ — proxy server that bot would use during authentication.
- *use_cookie* — means that bot would use cookies not to re-login every time it needs to push some request. Defaults as True.
- *cookie_fname* — filename where cookies would be stored. Default value: `cookie.txt`.

Example: `bot.login(username="YOUR_LOGIN", password="YOUR_PASSWORD")`

<a name="logout"></a> **logout** — Loggs you out.

### <a name="ids"></a> IDs

<a name="get_user_id_from_username"></a> **get_user_id_from_username** — Get `user_id` by username.

Parameters:

- _username_ — a string with user's Instagram username.

Example: `bot.get_you_medias("lego")`

Result: `196743444`

<a name="get_username_from_user_id"></a> **get_username_from_user_id** — Get username by `user_id`.

Parameters:

- *user_id* — Id of user that you want to fetch. See [get_user_id_from_username](#get_user_id_from_username).

Example: `bot.get_you_medias("196743444")`

Result: `lego`

<a name="get_media_id_from_link"></a> **get_media_id_from_link** — Get `media_id` by link on some Instagram post.

Parameters:

- _link_ — a string with a valid link on Instagram post.

Example: `bot.get_media_id_from_link("https://www.instagram.com/p/BryhSSgDEI5/")`

Result: `1941760781700579897`


<a name="get_link_from_media_id"></a> **get_link_from_media_id** — Get link on some Instagram post by `media_id`.

Parameters:

- *media_id* — See [get_media_id_from_link](#get_media_id_from_link)

Example: `bot.get_media_id_from_link(1941760781700579897)`

Result: `https://www.instagram.com/p/BryhSSgDEI5/`

### <a name="getmedias"></a> Get medias

<a name="get_user_medias"></a> **get_user_medias** — Get list of 20 last user's medias.

Parameters:

- *user_id* — Id of user that you want to fetch. See [get_user_id_from_username](#get_user_id_from_username).
- *filtration* — Bot would filter those publications, witch are not satisfies bot parameters as `max_likes_to_like` and `min_likes_to_like`. All medias between them would be displayed. Defaults as True.
- *is_comment* — Filtration of medias that has/hasn't a comment.

Example: `bot.get_user_medias("lego")`

Result: `[1900986973457183396, 1900986921481250054]`

<a name="get_your_medias"></a> **get_your_medias** — Get list of ids of your last medias.

Parameters:

- _as_dict_ — With parameter as_dict=True returns media as dict. False by default.

Example: `bot.get_you_medias()`

Result: `[1900986973457183396, 1900986921481250054]`

<a name="get_timeline_medias"></a> **get_timeline_medias** — Get list of media_ids from your timeline feed.

Example: `bot.get_timeline_medias()`

Result: `[1900986973457183396, 1900986921481250054]`

<a name="get_total_user_medias"></a> **get_total_user_medias** — Same as [get_user_medias](#get_user_medias), but fetches all of user's medias.

Parameters:

- *user_id* — Id of user that you want to fetch. See [get_user_id_from_username](#get_user_id_from_username).

<a name="get_hashtag_medias"></a> **get_hashtag_medias** — Get list of medias by hashtag.

Example: `bot.get_hashtag_medias("cats")`

Result: `[1900986973457183396, 1900986921481250054]`

<a name="get_geotag_medias"></a> **get_geotag_medias** — Get list of medias by geotag.

Example: `TODO`

### <a name="getusers"></a> Get users

<a name="get_timeline_users"></a> **get_timeline_users** — Get list of users from your timeline feed.

Example: `TODO`

<a name="get_hashtag_users"></a> **get_hashtag_users** — Get list of users who posted with hashtag.

Example: `TODO`

<a name="get_geotag_users"></a> **get_geotag_users** — Get list of users who posted with geotag.

Example: `TODO`

<a name="get_user_followers"></a> **get_user_followers** — Get list of user's followers.

Parameters:

- *user_id* — Id of user that you want to fetch. See [get_user_id_from_username](#get_user_id_from_username).

Example: `bot.get_user_followers("lego")`

Result: `['6976090614', '4828850852', '6986373483', '7139262982']`

<a name="get_user_following"></a> **get_user_following** — Get list of user's following.

Parameters:

- *user_id* — Id of user that you want to fetch. See [get_user_id_from_username](#get_user_id_from_username).

Example: `bot.get_user_following("lego")`

Result: `['1501782303', '871819364', '4804628891', '45786877']`

<a name="get_media_likers"></a> **get_media_likers** — Get list of media likers

Parameters:

- *media_id* — Id of post in Instagram that you want to fetch. See [get_media_id_from_link](#get_media_id_from_link).

Example: `bot.get_media_likers("1941760781700579897")`

Result: `['6976090614', '4828850852', '6986373483', '7139262982']`

<a name="get_media_commenters"></a> **get_media_commenters** — Get list of users who commented on the media

Example: `bot.get_media_commenters("1941760781700579897")`

Result: `['6976090614', '4828850852', '6986373483', '7139262982']`

### Comments

<a name="get_media_comments"></a> **get_media_comments** — Get list of 20 latest media's comments

Parameters:

- *media_id* Id of post in Instagram that you want to fetch. See [get_media_id_from_link](#get_media_id_from_link).
- *only_text* — option to get list with only text of each comment without additional information. Defaults as False.

Example: `bot.get_media_comments("1941760781700579897")`
Result is a list of such objects:
```
{'pk': 17848187965317794, 'user_id': 5726722318, 'text': 'Come glasgow', 'type': 0, 'created_at': 1545772239, 'created_at_utc': 1545772239, 'content_type': 'comment', 'status': 'Active', 'bit_flags': 0, 'user': {'pk': 5726722318, 'username': 'dj_gramm', 'full_name': 'KingJellyIG', 'is_private': True, 'profile_pic_url': 'https://scontent-iad3-1.cdninstagram.com/vp/b7e6505312f276c551b9b27c784d8080/5CB5D7D8/t51.2885-19/s150x150/46878995_2733544636871740_4791338569069232128_n.jpg?_nc_ht=scontent-iad3-1.cdninstagram.com', 'profile_pic_id': '1943181535717308400_5726722318', 'is_verified': False}, 'did_report_as_spam': False, 'share_enabled': False, 'has_liked_comment': False, 'comment_like_count': 0, 'inline_composer_display_condition': 'never'}
```

<a name="get_media_comments_all"></a> **get_media_comments_all** — Same as [get_media_comments](#get_media_comments), but with all comments.

<a name="get_comment"></a> **get_comment** — Get comment from comment file

Example: `bot.get_comment(17848187965317794)`
Result is a comment object:
```
{'pk': 17848187965317794, 'user_id': 5726722318, 'text': 'Come glasgow', 'type': 0, 'created_at': 1545772239, 'created_at_utc': 1545772239, 'content_type': 'comment', 'status': 'Active', 'bit_flags': 0, 'user': {'pk': 5726722318, 'username': 'dj_gramm', 'full_name': 'KingJellyIG', 'is_private': True, 'profile_pic_url': 'https://scontent-iad3-1.cdninstagram.com/vp/b7e6505312f276c551b9b27c784d8080/5CB5D7D8/t51.2885-19/s150x150/46878995_2733544636871740_4791338569069232128_n.jpg?_nc_ht=scontent-iad3-1.cdninstagram.com', 'profile_pic_id': '1943181535717308400_5726722318', 'is_verified': False}, 'did_report_as_spam': False, 'share_enabled': False, 'has_liked_comment': False, 'comment_like_count': 0, 'inline_composer_display_condition': 'never'}
```

### <a name="likes"></a> Likes

<a name="like"></a> **like** — Like media_id.

Example: `bot.like("1231241210")`

<a name="like_medias"></a> **like_medias** — Like medias from list.

Example: `bot.like_medias(["1323124", "123141245"])`

<a name="unlike"></a> **unlike** — Remove like from media.

Example: `bot.unlike("12321412512")`

<a name="unlike_medias"></a> **unlike_medias** — Remove likes from medias in list

Example: `bot.unlike_medias(["123", "321"])`

<a name="like_timeline"></a> **like_timeline** — Like medias from your timeline feed

Example: `bot.like_timeline()`

<a name="like_user"></a> **like_user** — Like last user's medias

Example: `bot.like_user("activefollower")`

<a name="like_hashtag"></a> **like_hashtag** — Like last medias with hashtag.

Example: `bot.like_hashtag("dog")`

<a name="like_geotag"></a> **like_geotag** — Like last medias with geotag

Example: `TODO`

### <a name="follows"></a> Follows

<a name="follow"></a> **follow** — Follow user.

Example: `bot.follow("activefollower")`

<a name="follow_users"></a> **follow_users** — Follow users from list.

Example: `bot.follow(["activefollower1", "activefollower2"])`

<a name="unfollow"></a> **unfollow** — Unfollow user.

Example: `bot.unfollow("competitor")`

<a name="unfollow_users"></a> **unfollow_users** — Unfollow users from list.

Example: `bot.unfollow_users(["competitor1", "competitor2"])`

<a name="unfollow_non_followers"></a> **unfollow_non_followers** — Unfollow users who don't follow you.

Example: `bot.unfollow_non_followers()`

### <a name="photos"></a> Photos

<a name="upload_photo"></a> **upload_photo** — Uploads photo to your account.

Example: `bot.upload_photo("/somephoto.jpg", caption="Nice pic!")`

<a name="download_photo"></a> **download_photo** — Downloads photo by id.

Example: `bot.download_photo(["123", filename="somefile.jpg")`

<a name="download_photos"></a> **download_photos** — Downloads photos by ids into given folder.

Example: `bot.download_photos(["123","345"], "photos")|`
