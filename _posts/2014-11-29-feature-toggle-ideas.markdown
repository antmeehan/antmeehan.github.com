---
layout:     post
title:      "FeatureToggle ideas"
subtitle:   "a.k.a. FeatureVersioning ideas"
date:       2014-12-04 21:00:00
author:     "Ant"
header-img: "img/post-bg-02.jpg"
comments:   true
---

<p>A bit of googling for this blog post and... it turns out that there is plenty of <a href="http://en.wikipedia.org/wiki/Feature_toggle">history</a> surrounding feature toggling already. In fact there is already an open-source .NET library <a href="https://github.com/jason-roberts/FeatureToggle">FeatureToggle</a> by <a href="https://github.com/jason-roberts">Jason Roberts</a> (who is also lives in Perth) which started back in 2012!</p>

<p>What does that mean for my project? For one I'll need to come up with a new name, as Jason already has dibs on the NuGet <a href="https://www.nuget.org/packages/FeatureToggle/" title="FeatureToggle on NuGet">package name</a> (including &gt;5,000 downloads!). Having a quick look at Jason's codebase it appears to be a sophisticated solution with plenty of extensibility points.</p>

<p>So should I <a href="https://help.github.com/articles/fork-a-repo/">fork?</a>. I know us software developers love to reinvent the wheel, but I do honestly think my thoughts around feature toggle are tangential to Jason's. So to reinforce that I am going to rename the project to <a href="http://antmeehan.com/FeatureVersioning">FeatureVersioning</a>. Why versioning? Well my latest experience with feature toggle was adding new functionality across a number of existing features &#8212; so we wanted to be able to toggle between the current and new version of different features across different environments. And most importantly, to be able release them to production in any order, and without a big-bang release.</p>

<p>What about new features? Well the non-existent feature can be considered version "0" and the first iteration version "1". As part of this project, I built a "dashboard" page which shows the defined features and their enabled versions across the environments, similar to the following:</p>

<style>
	.v1 {
		background-color: #D9EDF7;
	}
	.v2 {
		background-color: #DFF0D8;
	}
</style>

<table class="table table-bordered">
<tr>
	<th rowspan="2">Feature</th>
	<th>DEV</th>
	<th>DEV (Feature)</th>
	<th>TST</th>
	<th>TST (Feature)</th>
	<th>PROD</th>
</tr>
<tr>
	<td>v0.0.0.2802</td>
	<td>v0.0.0.2802</td>
	<td>v1.3.0.2525</td>
	<td>v1.3.0.2525</td>
	<td>v1.2.0.1843</td>
</tr>
<tr>
	<th>Calculator</th>
	<td class="v1">1</td>
	<td class="v2">2</td>
	<td class="v1">1</td>
	<td class="v2">2</td>
	<td class="v1">1</td>
</tr>
<tr>
	<th>Editor</th>
	<td class="v1">0</td>
	<td class="v2">1</td>
	<td class="v1">0</td>
	<td class="v2">1</td>
	<td class="v1">0</td>
</tr>
<tr>
	<th>UserManager</th>
	<td class="v1">2</td>
	<td class="v2">3</td>
	<td class="v1">2</td>
	<td class="v1">2</td>
	<td class="v1">2</td>
</tr>
</table>

<p>In the above example we have 5 environments:</p>
<ul>
	<li><i>DEV:</i> This is where your CI deploys to, with the same feature versioning as PROD, to allow you to perform regression testing etc.</li>
	<li><i>DEV (Feature):</i> CI also deploys to this environment, but feature versions are set to the latest for all features, to allow early access to new feature versions.</li>
	<li><i>TST:</i> Gated deployments (perhaps by the test team), with the same feature versioning as PROD, to allow you to perform regression testing etc.</li>
	<li><i>TST (Feature):</i> Also gated deployments, with features set to the latest version for those currently being tested.</li>
	<li><i>PROD:</i> Production, with feature versions set to those which have been signed off.</li>
</ul>
<p>In our example, we are actively testing new versions of the Calculator and Editor features. There is also a brand new feature UserManager which isn't ready for testing, but can be accessed in the <i>DEV (Feature)</i> environment.</p>

<p>So now we have the general concepts of FeatureVersioning, what support do we want in our new library? That's for the next post.</p>