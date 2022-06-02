---
title: "【WordPress】wp-login.php?action=lostpasswordをリダイレクトさせる"
emoji: "💡"
type: "tech"
topics: ["php", "wordpress"]
published: true
---

# 背景
WP-Membersで「パスワードを忘れた方」のリンク先は`wp-login.php?action=lostpassword`になっているが、パスワードリセット画面のショートコードを埋め込んだ固定ページに遷移させたかった。

# 試したこと
WordPressのリダイレクトでググるとこんな感じのがよく出てきます。
URLの文字列を取得して、`wp_redirect`でいけるかと思いきや無理でした...

```php:functions.php
add_action( 'get_header', 'specified_url_redirect' );
function specified_url_redirect(){
	$url = $_SERVER['REQUEST_URI'];
	if(strstr($url,'wp-login.php?action=lostpassword')){
		wp_redirect( get_site_url('/lostpassword'), 301 );
		exit;
	}
}
```

# 実現できたコード

フィルターで`lostpassword_url`を使ってフックさせるといけました。

```php:functions.php
add_filter( 'lostpassword_url', 'my_lost_password_page', 10, 2 );
function my_lost_password_page( $lostpassword_url, $redirect ) {
    return home_url( '/lostpassword' . $redirect );
}
```

# 参考ページ
https://developer.wordpress.org/reference/hooks/lostpassword_url/