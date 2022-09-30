# Load Balancer Strategy

Suppose you are implementing the load balancing strategy for a nginx-liked web server. Given a list of ip [1, 2, 3], return the next round-robined result.

# Basic Version

At the first glance, we can use a counter to track the number of the next ip.

<div class="markdown-tabs">
<ul class="nav nav-tabs" role="tablist">
<li role="presentation">
<a href="#tab-1-go" aria-controls="tab-1-go" role="tab" data-toggle="tab">GoLang</a>
</li>
<li role="presentation">
<a href="#tab-1-cpp" aria-controls="tab-1-cpp" role="tab" data-toggle="tab">C++</a>
</li>
</ul>

<div class="tab-content">
<div role="tabpanel" class="tab-pane" id="tab-1-go">
{% github_embed "https://github.com/kleon1024/crack-coding/blob/7768a763a957498d6db5ab3cc422f99fffe6752e/golang/concurrency/lb.go" %}{% endgithub_embed %}
</div>
<div role="tabpanel" class="tab-pane" id="tab-1-cpp">
{% github_embed "https://github.com/kleon1024/crack-coding/blob/7e36a6ecbb6863d2749097935f518348e8db26b2/golang/concurrency/lb-con.go" %}{% endgithub_embed %}
</div>
</div>
</div>

# Concurrency Version

We could use a mutex lock to protect the counter.

{% github_embed "https://github.com/kleon1024/crack-coding/blob/7e36a6ecbb6863d2749097935f518348e8db26b2/golang/concurrency/lb-con.go" %}{% endgithub_embed %}

# Grouped Ips

Follow-Up: Suppose ips are grouped. e.g. A: [1, 2, 3], B: [1, 4, 5]. Get the next round-robined result for the specified group combination.
Input A means selecting from the group A. Input B means select from the group B. Input AB means select from the intersection of group A and B. Empty means select from all ips.

