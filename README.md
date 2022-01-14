# Anatole Theme for Zola

Port [Anatole theme for farbox](https://github.com/hi-caicai/farbox-theme-Anatole) to Zola.

![screenshot](./screenshot.png)

![screenshot-mobile](./screenshot-mobile.png)

You can view my blog for an example configuation, with customizations.

## Installation

First download this theme to your `themes` directory:

```bash
$ cd themes
$ git clone https://github.com/longfangsong/anatole-zola.git
```
and then enable it in your `config.toml`:

```toml
theme = "anatole-zola"
```

And copy the `content/about`, `content/archive`, `content/_index.md` in the theme folder to your own content folder. And edit the `_index.md` in `about` folder to edit the content of your `about` page.

## Options

### Basic

Add `title`, `description` and `base_url`:

```toml
title = "Anatole"
description = "A other zola theme"
base_url = "https://example.com"
```

### Language

Currently, we have English, Chinese and German translation, set the `default_language` if necessary:

```toml
# 如果你想要中文
default_language = "zh"
```

It's sad that translations in themes are not working, you can copy these to your `config.toml`:

```toml
[languages.en.translations]
about = "About"
home = "Home"
tags = "Tags"
archive = "Archive"
links = "Links"
next_page = "Next Page"
last_page = "Last Page"

[languages.zh.translations]
home = "首页"
about = "关于"
tags = "标签"
archive = "归档"
links = "友链"
next_page = "下一页"
last_page = "上一页"

[languages.de.translations]
about = "Info"
home = "Home"
tags = "Kategorien"
archive = "Archiv"
links = "Links"
date_format = "%d-%m-%Y"
next_page = "Nächste Seite"
last_page = "Vorherige Seite"
```

Feel free to create a pull request if you want to translate the promotes into other languages!

### Sections

Tags and links sections are optional.

- If you want to enable the tags page, add
  ```toml
  taxonomies = [
    {name = "tags"},
  ]

  [extra.show]
  tags = true
  ```
  To your `config.toml`

- If you want to enable the links page, add

  ```toml
  [extra.show]
  links = true
  ```

  and copy `content/links` to your own `content` library. And edit the `_index.md` in it to edit its content.

- If you want to add the author's name on each page, add:

  ```toml
  [extra]
  author = "John Doe"
  ```

### Sidebar menu

We support a bunch of social links, they are:

```toml
[extra.social]
github = ""
stackoverflow = "" # use user_id
twitter = ""
facebook = ""
instagram = ""
dribbble = ""
weibo = ""
linkedin = ""
flickr = ""
```

Fill in your username if you want! And the logo won't appear if you leave it empty.



### Comment system

We currently support [valine](https://valine.js.org/quickstart.html):

```toml
[extra.comment.valine]
appid = "Your appid goes here"
appkey = "Your appkey goes here"
notify = false # true/false: mail notify https://github.com/xCss/Valine/wiki/Valine-%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F%E4%B8%AD%E7%9A%84%E9%82%AE%E4%BB%B6%E6%8F%90%E9%86%92%E8%AE%BE%E7%BD%AE
verify = false # true/false: verify code
avatar = "mm" # avatar style https://github.com/xCss/Valine/wiki/avatar-setting-for-valine
placeholder = "Say something here"
```

[disqus](https://disqus.com/admin/create/), note disqus does not work in Mainland China:

```toml
[extra.comment.disqus]
name = "longfangsong"
```

And [utterances](https://utteranc.es/):

```toml
[extra.comment.utterances]
repo = "Your repo for comments"
issue_term = "pathname"
theme = "github-light"
```


## Customize

There are several points I left in the origin templates for you to customize your site.

### More style

You can create a `blog.scss` or something similiar in the your `sass` folder, add a `templates.html` with following content:

```html
{% extends "anatole-zola/templates/basic.html" %}
{% block extra_head %}
<link rel="stylesheet" href="{{ get_url(path="blog.css") }}">
{% endblock %}
```

### More social links

You can add more social links by adding a `templates.html` with some content added to `more_social_link` block:

```html
{% extends "anatole-zola/templates/basic.html" %}
{% block more_social_link %}
<div id="pirate" data-wordart-src="//cdn.wordart.com/json/685czi4rqil5" style="width: 100%;" data-wordart-show-attribution></div>
{% endblock %}
```

If you want to use some awsome logos, [font awsome icons](https://fontawesome.com/icons?d=gallery) are already available.
