# 사용 지침 사항

**중요! 이 지침사항을 처음부터 끝까지 읽고 실행하세요! 행운을 빕니다!**

## 어떻게 작동시키나요?

당신은 프로젝트를 다운로드 받아야 합니다. ***instabot/examples/*** 폴더 안에 당신히 실행해야할 스크립트 들이 있습니다. 

## 이 스크립트를 어떻게 실행시켜야 하나요?

실행 프롬프트를 열고,  ***cd*** 명령어를 사용하여 프로젝트 디렉토리로 이동합니다. 즉, ***instabot/examples*** 이라고 쳐서 이동하세요.

``` python
python name.py param
```

***name*** 이 이 스크립트의 이름이고, ***param*** 이 스크립트를 실행하기 위해 필요한 매개변수 입니다. 모든 스크립트가 파라미터가 필요한 것은 아닙니다.

## 스크립트에 입력할 매개변수가 필요한지 어떻게 알 수 있을까요?

입력해서 스크립트를 실행하세요.

``` python
python name.py
```

만약 여기에 필요한 매개변수가 없다면, 스크립트는 중단되고 에러를 보여줄 것입니다.
예제.
스크립트를 실행하세요.

``` python
python like_hashtags.py. 
```

스크립트는 중단되고 메세지를 보여줄 것이다. :

``` python
error: the following arguments are required: hashtags.
```

이 의미는 우리가 해시태그가 필요하다는 뜻이다. 올바른 예제:

``` python
python like_hashtags.py follow
```

## 모두 포함

***multi_script_CLI.py*** 는 모든 함수가 포함된 스크립트이다. 이것을 처음 실행하면, 스크립트를 구성하라는 프롬프트가 표시됩니다. 스크립트의 설정사항은 ***setting.txt*** 파일에 저장되었습니다. 또한 파일들이 생성될 것입니다: ***hashtag_file.txt, users_file.txt, whitelist.txt, blacklist.txt, comment.txt***.

## 24/7

그렇다, 특정 사용자와 구독자의 구독을 24시간 내내 수집하는 스크립트가 있고, 또한 닉네임과 해시태그로 사진에 좋아요를 누릅니다. 이 모든 것들은 ***ultimate.py*** 스크립트를 허용합니다. 이 스크립트는 ***instabot/examples/ultimate*** 에 있습니다. 폴더에는 스크립트를 실행하기 위한 다른 텍스트 파일도 들어 있습니다. 이 파일들에서 새로운 매개변수들은 각각 새로운 줄에 써야합니다.

## 스케쥴

또한 하루 종일 작동할 스크립트가 있지만, 이 스크립트는 계획에 따라 작동합니다. 이 스크립트는 ***instabot/examples/ultimate_schedule*** 폴더에 있는 ***ultimate.py*** 입니다. 당신은 아무 에디터나 사용하여 파일을 열고 수정할 수 있습니다. 코드의 중요한 부분에 주석이 있기 때문에 이 과정은 쉽습니다. 

## 스크립트를 올바르게 구성하는 방법

당신의 계정이 차단당하지 않는 것을 보장하기 위해서, 스크립트 예제를 구성해야 합니다. 우리가 매 분마다 해시태그에 사진을 저장해야 한다고 가정해봅시다. 먼저 시간 단위를 초로 해주세요. 텍스트 에디터로 ***like_hashtags.py*** 파일을 열어봅시다. 다음과 같은 라인을 찾아봅시다. (이 라인은 대략적으로 누군가 찾아보아야 합니다).

``` python
bot = Bot()
bot.login(username=args.u, password=args.p,
          proxy=args.proxy)
```

다음에 이 내용을 적어봅시다.

``` python
bot = Bot()
```

괄호 안에 매개변수를 써야 합니다. 이 매개 변수는 ***like_delay*** 입니다. (왜냐면) 우리는 봇이 매 분마다 사진의 해시태그에 만족하기 때문에 이 매개변수는 60으로 설정되어야 합니다. 끝으로, 이런식으로 보일 것입니다.

``` python
bot = Bot(like_delay=60)
bot.login(username=args.u, password=args.p,
          proxy=args.proxy)
```

## 매개변수 목록 

| parameter| description | example |
| ------------- |:-------------:| ------:|
| proxy | Instabot의 프록시  | None|
| max_likes_per_day| 봇이 하루에 좋아요를 누를 수 있는 최대값| 1000|
| max_unlikes_per_day | 봇이 하루에 좋아하지 않을 미디어의 최대값 | 1000|
| max_follows_per_day| 하루에 팔로우 할 수 있는 최대값| 350|
| max_unfollows_per_day| 하루에 언팔로우를 할 수 있는 최대값| 350|
| max_comments_per_day| 하루에 댓글을 남길 수 있는 최대값| 100|
| max_likes_to_like| 게시글이 이 값보다 더 많은 좋아요를 받았다면, 이는 무시될 것이고 좋아요를 누르지 않는다.  | 200|
| filter_users | True일 경우 사용자 필터링 | True|
| max_followers_to_follow| 사용자가 이 값보다 더 많은 팔로워를 보유하고 있다면, 사용자는 팔로우 되거나 좋아요를 받지 않을 것이다. | 2000|
| min_followers_to_follow| 사용자가 이 값보다 더 적은 팔로워를 보유하고 있다면, 사용자는 팔로우 되거나 좋아요를 받지 않을 것이다.| 10|
| max_following_to_follow| 사용자가 이 값보다 더 많은 팔로잉을 하고 있다면, 사용자는 팔로우 되거나 좋아요를 받지 않을 것이다.| 10000|
| min_following_to_follow| 사용자가 이 값보다 더 적은 팔로잉을 하고 있다면, 사용자는 팔로우 되거나 좋아요를 받지 않을 것이다.| 10|
| max_followers_to_following_ratio| 사용자의 (팔로워수/팔로잉)가 이 값보다 크다면, 사용자는 팔로우 되거나 좋아요를 받지 않을 것이다. | 10|
| max_following_to_followers_ratio| 사용자의 (팔로잉/팔로워수)가 이 값보다 크다면, 사용자는 팔로우 되거나 좋아요를 받지 않을 것이다.| 2|
| min_media_count_to_follow| 사용자의 게시글 수가 이 값보다 적다면, 사용자는 팔로우 되지 않을 것이다. | 3|
| max_following_to_block| 사용자가 이 값보다 더 많은 팔로잉을을 하고 있다면, 사용자는 massfollower(많은 사람들을 팔로우하고 있는 사람)이기 때문에 블락 스크립트에 블락 될것이다. | 2000|
| max_likes_to_like | 게시글이 좋아요를 받을 수 있는 좋아요의 최대 값 | 100 |
| like_delay | 좋아요를 누르는데 걸리는 지연 시간(second)| 10|
| unlike_delay | 좋아요를 해제하는데 걸리는 지연 시간(second) | 10|
| follow_delay | 팔로우하는데 걸리는 지연 시간(second) | 30|
| unfollow_delay | 언팔로우하는데 걸리는 지연 시간(second) | 30|
| comment_delay | 댓글을 다는데 걸리는 지연 시간(second) |  60|
| whitelist | 언팔로우 하면 안되는 사용자들을 모은 파일의 경로 | "whitelist.txt"|
| blacklist | 팔로우 하면 안되는 사용자들을 모은 파일의 경로 | "blacklist.txt"|
| comments_file | 댓글 데이터베이스의 경로 | "comments.txt" |
| stop_words| 정지 할 단어들의 목록: 사용자의 설명에 이러한 정지 할 단어가 있다면 해당 사용자를 팔로우 하지 않습니다.| ['shop', 'store', 'free']|























