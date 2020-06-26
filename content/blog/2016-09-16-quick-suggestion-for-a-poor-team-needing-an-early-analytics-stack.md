+++
author = "karl taylor"
categories = ["analytics", "marketing"]
date = "2016-09-16T18:42:33"
title = "Quick Suggestion For A Poor Team Needing An Early Analytics Stack"
type = "post"
+++

  ![](https://raw.githubusercontent.com/karljtaylor/kjt/blog/content/assets/e62b1-1a76esfsqohzbbtzsptq-mq.png)  


 I think all too often, startups put off putting in basic tracking capabilities until they feel like they can afford a solution on the level of [Adobe Marketing Cloud](http://www.adobe.com/marketing-cloud.html) — or in the medium term [HubSpot](https://medium.com/u/8732e73183e5).

 I think if I were just getting started on a project this is the flow I’d use. (It’s actually the flow we’re using on our team’s branded properties right now.)

  2. Install [Segment](https://medium.com/u/6e946b6a2866).
  I really shouldn’t be so shameless, but if I were going to deploy a tag on an early stage team (say an early website) I wouldn’t want to have to revisit updating my site each time I discovered a new capability I wanted to play with.

 You’re likely going to be doing a lot of that in the beginning. It’s a good idea to get started in a way that you’re going to find useful as you go on.

 (You could also definitely wrestle with Google tag manager. [9 Clouds](https://medium.com/u/109d780a5963) has a solid primer going on [here](https://medium.com/@9clouds/the-complete-guide-to-google-tag-manager-abridged-e8ce8a3e0eed#.wnkx2fzic).)

 2. Integrate The Properties You’re Currently Using

 It’s likely that you’ve got a Facebook page, and probably a Twitter account. You should take the opportunity to get signed up at [business.facebook.com](http://business.facebook.com) and follow their directions to setup a pixel. (I like [this guide](https://medium.com/retargetapp-shopify-app/the-ultimate-guide-to-facebook-retargeting-dbbbdf138996#.etrrltzcm) from [Pavel Matvienko](https://medium.com/u/e727d044eabe))

 You’ll find that the fine folks at [Segment](https://medium.com/u/6e946b6a2866) have a number of delightful guides that should work you through updating the settings for each integration — which in the short term will save you from having to make additional changes to your website.

 You don’t have to go crazy here, because you’ll find you’re in a plan that’s priced by MTUs, which if you’re finding this advice useful, you’re a ways off from having a big number of.

 3. Website? [Google Analytics](https://analytics.google.com/analytics/web/). App? [Mixpanel](http://mixpanel.com).

 In both cases, you should settle pretty near to the free tier — it takes a while to outgrow.

 If you want to drill a little deeper, here’s a [good introduction to Segment](https://medium.com/saas-user-onboarding-resources/how-to-hack-your-analytics-with-segment-io-500acfc32254#.vjxawm19d) from [Francois de Fitte](https://medium.com/u/dbb26c48469).


     <form style="border:1px solid #ccc;padding:3px;text-align: center;" action="https://tinyletter.com/karljtaylor" method="post" target="popupwindow" onsubmit="window.open('https://tinyletter.com/karljtaylor', 'popupwindow', 'scrollbars=yes,width=800,height=600');return true" _lpchecked="1">
      <p style="
       display: flex;
       align-items: center;
       flex-direction: column;
   "><label for="tlemail">Never miss an update! Enter your email address to subscribe!</label>
        <input type="text" name="email" id="tlemail" style="
       width: 140px;
   "></p>
      <input type="hidden" value="1" name="embed"><input type="submit" value="Subscribe Now">
   </form>
