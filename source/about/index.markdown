---
layout: page
title: "About me"
comments: false
sharing: false
footer: false
---
I am a full stack web developer, by day and by night. I like to code things, a
lot; especially if they interact with the network.

Passioned about writing aesthetic and efficient code using the latest languages
and frameworks, I always end up spending a more than reasonable part of my free
time doing random projects like implementing some Internet protocol with
Node.js or a chess algorithm in C++11.

Shiny new stuff are most appealing to me but I try not to forget that they will
become old rather sooner than later, and that only time can tell if they will
mature gracefully or be discarded. So I seek knowledge in the tremendous
quantity of electronic archives accumulated over time by generations of awesome
developers and I jump at every opportunity to learn the history of Computer
Science by reading classic papers or obsolete RFCs.

Finally, this short introduction would be incomplete without mentioning my
strong belief in the importance of Free and Open Source Software. We are all
standing on the shoulders of giants, every little pieces of original material
we produce should be given back to the community without whom there would be
nothing in the first place.

Now that you know a little more about me, I hope that you will be interested by
some of my [projects](/projects) or at least the languages and frameworks I use
to build them. I also to try to [blog](/blog/archives) about all this when I
find something worth sharing.

You can find me on [GitHub](https://github.com/vinc) and
[Twitter](https://twitter.com/vinc686) and you can also write to
[me@domain](mailto://me@domain).

<script>
(function() {

  String.prototype.antispam = function() {
    return this.replace('domain', document.location.hostname);
  };

  $(document).ready(function() {
    var email = $('[href^=mailto]');
    email.attr('href', email.attr('href').antispam());
    email.text(email.text().antispam());
  });

}).call(this);
</script>
