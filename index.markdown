---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
<h2>Leetcode</h2>
<p>Here is a list of leetcode problems that I have explored.</p>


<table>
  <tr>
    <th>#</th>
    <th>Title</th>
    <th>Level</th>
    <th>Topic</th>
    <th>Date</th>
  </tr>

  {% for post in site.posts %}
    <tr>
        <td> {{ post.number }}</td>
        <td> <a href="/leetcode/{{ post.url }}">{{ post.title }} </a></td>
        <td> {{ post.level }}</td>
        <td> {{ post.topic }}</td>
        <td> {{ post.workDate }}</td>
    </tr>
  {% endfor %}
</table>