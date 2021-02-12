+++
title = "最新ページ"
+++

<h2>新着記事</h2>
<ul>
  {{ range first 1 .Site.RegularPages.ByDate.Reverse }}
    <li>
      <b><a href="{{.RelPermalink}}">{{.Title}}</a></b>
      <time>{{.Date.Format "2006-01-02"}}</time>
    </li>
  {{ end }}
</ul>
