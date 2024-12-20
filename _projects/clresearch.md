---
layout: page
title: Investigating the impact of model architecture on continual learning performance
description: How do ResNet models with differing depth and width fare in catastrophic forgetting?
image: assets/images/net.jpeg
nav-menu: false
show_tile: true
order: 10
---

<!-- Main -->
<div id="main" class="alt">

<!-- One -->
<section id="one">
	<div class="inner">
		<header class="major">
			<h1>Investigating the impact of model architecture on continual learning performance</h1>
		</header>
		{% if page.image %}<span class="image main"><img src="{{ site.baseurl }}/{{ page.image }}" alt="colorful nets against black background" /></span>{% endif %}
<!-- Content -->
<h2 id="content">Overview</h2>
<p><strong>Continual Learning (CL)</strong> focuses on enabling models to learn from new data streams over time while preserving past knowledge. Continual Learning seeks to minimize catastrophic forgetting, a critical phenomenon in which deep learning models forget previously trained information upon being training on new data. <strong>Online Continual Learning (OCL)</strong> evolves this concept by adapting models to learn from ongoing small batches of data in real-time. Online Continual Learning strives for a balance between acquiring new information and retaining old knowledge in dynamic environments.</p>

<p>This study investigates the impact of model size on online continual learning performance and forgetting, using the SplitCIFAR-10 continual learning benchmark. I trained and evaluated ResNet architectures of varying sizes and widths to examine how network size affects model performance in an online continual learning setting (class-incremental learning).</p>

<p>Key findings show that <strong>larger models do not necessarily guarantee better continual learning performance</strong>; in fact, they often struggle more in adapting to new tasks, particularly in online settings. These results challenge the existing notion that larger models inherently mitigate catastrophic forgetting, highlighting the nuanced relationship between model size and continual learning efficacy. This study contributes to a deeper understanding of model scalability and its practical implications in continual learning scenarios.</p>

<p><a href="https://arxiv.org/abs/2407.00176" class="button">See paper on arxiv</a></p>

<br />

<h2 id="content">Key Findings</h2>
<div class="row">
	<div class="6u 12u$(small)">
		<strong>Accuracy decreases as model size increases</strong>
		<p>Average Anytime Accuracy (AAA) measures the effectiveness of the model across all stages of training, rather than at a single endpoint, offering a more comprehensive view of its learning trajectory.</p>
	</div>
	<div class="6u$ 12u$(small)">
		<img src="{{ '/assets/images/AAA_on_off.png' | relative_url }}" alt="chart" data-position="center center" />
	</div>
</div>

<div class="row">
	<div class="6u 12u$(small)">
		<strong>Accuracy of larger models grow at a slower pace when training</strong>
		<p>The rate to which validation stream accuracy increases with each task degrade with larger models. Slim-ResNet18 shows the highest accuracy and growth trend. This could indicate that larger models are worse at generalizing to a class-incremental learning scenario.</p>
	</div>
	<div class="6u$ 12u$(small)">
		<img src="{{ '/assets/images/stream_acc1.png' | relative_url }}" alt="chart" data-position="center center" />
	</div>
</div>

<div class="row">
	<strong>Forgetting levels show more nuanced results</strong>
		<p>This differences in forgetting between online and offline CL setting is aligned with the accuracy metrics earlier, where the performance of ResNet50 decreases more starkly in the online CL setting. Future studies could increase training cycles to lead to more insights.</p>
	<div class="6u 12u$(small)">
		<img src="{{ '/assets/images/forgetting_online.png' | relative_url }}" alt="chart" data-position="center center" />
	</div>
	<div class="6u$ 12u$(small)">
		<img src="{{ '/assets/images/forgetting_offline.png' | relative_url }}" alt="chart" data-position="center center" />
	</div>
</div>


<strong>Saliency maps reveal hints on how the models read the inputs</strong>
<p>When it comes to the ability to highlight intuitive areas of interest in the images, there seemed to be a noticeable improvement from ResNet18 to ResNet34, but this was not necessarily the case from ResNet34 to ResNet50.</p>
<img src="{{ '/assets/images/saliency_online.png' | relative_url }}" alt="chart" data-position="center center" />

<hr class="major" />

<!-- <p><a href="">See paper on arxiv</a></p> -->

<h4>Details</h4>
<ul>
	<li>When: Fall 2023</li>
	<li>This study was completed as a final project for the graduate course <a href="https://phillipi.github.io/6.s898/">6.S898 Deep Learning</a> at MIT.</li>
</ul>


</div>
</section>


</div>
