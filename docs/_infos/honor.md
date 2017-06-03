---
title: Honor
---

## Honor

Honor represents the level of respect a user has earned from the community, based on their skill and contributions.
Honor is earned fastest through creating kata, crafting great solutions, and constructive comments.

The following table shows all of the honor you can earn.

<table class="f6 w-100 mw6 center" cellspacing="0">
  <thead>
    <tr><th class="pt3 pb3 pl4 tl">Reason</th><th class="pt3 pb3 pr4 tr">Honor</th></tr>
  </thead>

  <tbody class="lh-copy">
  {% for row in site.data.honor_points %}
    <tr class="stripe-dark">
      <td class="pt3 pb3 pl4 tl">{{ row.reason }}</td><td class="pt3 pb3 pr4 tr">{{ row.points }}</td>
    </tr>
  {% endfor %}
  </tbody>
</table>

### Privileges

As you increase your honor, you will be rewarded with additional site privileges.

The following table shows all of the privileges you can earn.

<table class="f6 w-100 mw6 center" cellspacing="0">
  <thead>
    <tr><th class="pt3 pb3 pl4 tl">Privilege</th><th class="pt3 pb3 pr4 tr">Required Honor</th></tr>
  </thead>

  <tbody class="lh-copy">
  {% for row in site.data.privileges %}
    <tr class="stripe-dark">
      <td class="pt3 pb3 pl4 tl">{{ row.name }}</td><td class="pt3 pb3 pr4 tr">{{ row.points }}</td>
    </tr>
  {% endfor %}
  </tbody>
</table>
