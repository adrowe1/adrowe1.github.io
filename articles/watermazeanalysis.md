---
layout: jumbotron
title: Dredging the watermaze
categories: article
heading1: Extracting detailed information from the data gathered during watermaze studies of learning and memory in mice.
heading2: Working draft of manuscript
---

####Abstract

<div class="row">
	<div class="col-md-12">
    <p> Learning and memory in mice are commonly tested using the Morris water maze. Mice are released from the edge of the pool and allowed to swim for 60&nbsp;s in search of a submerged platform. Since mice do not like water, they are assumed to prefer being on the platform. This process is repeated 32 times in the space of four days, with the start point pseudo-randomly alternating between four points around the edge of the pool. As the trials progress, it is assumed that the mice learn the position of the platform, and therefore choose a more direct swimming route. Thus the rate of improvement in the time required to find the platform (platform latency to first entry) is taken as a measure of learning ability. </p> 
    <p> In this study I have taken the raw positional data from 120&nbsp;mice (C57BL/6 background) with seven different genotypes and examined the paths swum by each mouse for signs of learning. The raw data shows behaviour which is a great deal more complex than standard analysis suggests. <b> It is in fact extremely rare for a mouse to swim directly to the platform even after it has successfully performed many trials. </b> A detailed discussion of what can be determined by these methods is presented below, but there are two novel conclusions which can be drawn. </p>
    <p> First, the swimming behaviour shows strong traits of anxiety, and a genotype-dependent adaptation to this anxiety over time. Quantifying anxiety in the watermaze correlates well with anxiety measured in the open field test and is negatively correlated with the platform latency to first entry. Thus the time required to find the platform measures an interaction between anxiety and learning. Without controlling for anxiety in the Morris water maze it is very likely that what is being measured is actually the genotype's rate of adaptation to anxiety, rather than meaningful learning. </p>
    <p> Second, and more interestingly, I observe an extremely striking tendency in the memory retention testing data taken on days 5 and 12. These two trials start from a previously unused point and the latency to platform is measured. Again the anxiety problem exists, so increased latencies a week later may only be measuring a higher rate of anxiety de-acclimatization, rather than forgetfulness. Irrespective of this, however, there is an incredible similarity between the two paths swum by any one mouse, with a seven day interval between trials. While most ecology studies of animal navigation show relatively simple and qualitatively similar paths through complex landscapes, a mouse swimming in a circular pool follows a relatively complex path in the simplest possible landscape. Rather than triangulating on the visual cues and using them to navigate to the platform, it appears that the mice have a strong tendency to closely follow the path they swam a week earlier, even if it is extremely inefficient for reaching the platform. While this would be easy to perform in a complex landscape with physical barriers and many visual cues, swimming a repeat of a complex path one week later seems like a much harder navigational task (in human terms) than any other approach. This suggests that a mouse's spatial memory differs from human spatial memory and may be more dynamically visual, allowing the mouse to retrace its tracks in space as though it were constantly able to compare its position with a video record of its previous path. We can also speculate as to whether this behaviour is a stress-related strategy, whereby a known path to safety (they are conditioned to expect rescue after a maximum of 60&nbsp;s) is chosen automatically in a panic, in preference to any rational attempt to navigate. </p>

  </div> 
</div>

----------------

####Introduction

<div class="row">
	<div class="col-md-12">
      <div class="col-xs-7 col-md-7 pull-right">
        <div class="row">
          <a href="/articles/watermaze/wrong.png" data-toggle="lightbox" data-gallery="multiimages" data-title="Figure 1A: Typical presentation of learning data" data-footer="Learning in the Morris water maze is typically presented as shown above. This figure gives the impression of significant differences in the rate of learning, but this approach and the methods used to determine statistical significance are something of a minefield." class="col-sm-6">
          <img src="/articles/watermaze/wrong.png" class="img-responsive">
          </a>
          <a href="/articles/watermaze/raw.latencies.png" data-toggle="lightbox" data-gallery="multiimages" data-title="Figure 1B: Raw latency to platform in learning data" data-footer="Raw latencies to platform are shown for all seven genotypes analysed. Comparing the first three genotypes (WT, A and B) with the presentation of the same data in figure 1A gives far weaker grounds to conclude that there are significant differences in learning. While there are apparent trends, with the median level falling faster for some genotypes, the level of variation and the number of mice which do not find the platform within 60&nbsp;s means that the data cannot be presented correctly by the methods used in figure 1A. " class="col-sm-6">
          <img src="/articles/watermaze/raw.latencies.png" class="img-responsive">
          </a>
          
        </div>
	   	<p> <i> Figure 1: Learning in the Morris water maze is measured as a progressive decrease in the time required for mice to swim to a hidden platform and is typically presented as shown in 1A (left). This is a great oversimplification of the raw data shown in 1B (right) and often incorrectly handles right-censored data. </i> </p>
      </div>


      <p>The Morris water maze is commonly (<a href="http://www.ncbi.nlm.nih.gov/pubmed/?term=%22morris+water+maze%22">5145 hits on PubMed</a> on 17.03.2014) used to measure learning and memory in mice. Over a period of 4 days, mice are released according to the <a data-toggle="collapse" data-parent="#accordionAbstract" href="#collapseProtocol">protocol</a> shown below and the time required to swim to the submerged platform (platform latency to first entry) is recorded. The layout of the maze with start points is shown <a data-toggle="collapse" data-parent="#accordionAbstract" href="#collapseStarts">below</a>.  </p>

      <p>There are varying standards for the analysis of these data as discussed in more detail <a data-toggle="collapse" data-parent="#accordionAbstract" href="#collapseLiterature">below</a>, but this is not the primary focus of this study, although I cover it in some detail <a data-toggle="collapse" data-parent="#accordionMethods" href="#collapseStandardImprove">later</a>. The fact remains that the entire exploration and learning process undergone by any one mouse, over four consecutive days, is reduced from a detailed positional dataset with sub 0.125s time resolution, to 32 data points.  </p>

      <p>The main motivation for this study was to use all of the available detail in the experimental data to refine and confirm the behavioural conclusions we draw. Therefore we extracted all of the raw tracking data from the <a href = "http://www.any-maze.com/" target="_blank">Any-Maze</a> data files for 120 mice with 7 different genotypes, to discover how these data relate to the simple latency measure. </p>

      <p>The following relations have been investigated. The dependence of swimming speed upon position (proximity to the wall of the maze), time (do they swim constantly or intermittently) and genotype. How starting position affects the rate of successful platform discovery. How individuals develop a strategy to find the platform. How navigational strategies relate to success or failure of the platform search. How paths can be parameterized to determine differing strategies.</p>

      <hr>

  <p>The following points should be taken into consideration when analysing watermaze data.</p>
  
    <ul>
      <li >Mice do not like swimming, therefore it is reasonable to expect that they want to escape from the watermaze.</li>
      <li>If they want to escape, they are likely stressed, which means that they are probably learning whilst anxious. </li>
      <li >The association of latency with learning is presumably based upon the rational assumption that mice want to minimize the time spent swimming and that they will therefore choose the shortest path to the platform. We should consider the possibility that sufficiently anxious mice respond purely instinctively, rather than rationally. </li>
      <li >While most ecology studies of animal navigation show relatively simple and qualitatively similar paths through complex landscapes, a mouse swimming in a circular pool follows a relatively complex path in the simplest possible landscape.</li>
    </ul>


       </div> 
</div>




<div class="row">
  <div class="col-md-12">
          
    <div class="panel-group" id="accordionAbstract">
     <div class="panel panel-default">
       <div class="panel-heading">
         <h4 class="panel-title">
           <a data-toggle="collapse" data-parent="#accordionAbstract" href="#collapseProtocol">
             Morris Water Maze training and testing protocol
           </a>
         </h4>
       </div>
       <div id="collapseProtocol" class="panel-collapse collapse">
         <div class="panel-body">
           <p>The MWM (Vorhees and Williams, 2006) task was performed in a randomized order when the mice were&nbsp;6&nbsp;months of age. The trials were carried out in a white circular pool 120&nbsp;cm in diameter, 30&nbsp;cm deep and filled with 20&nbsp;cm of white opaque water (SikaLatex liquid, Sika, Norway) kept at 22 ± 1°C. A pneumatically controlled escape platform, 11&nbsp;cm in diameter, was located at a fixed position halfway between the midpoint of the pool and the wall.
           During training trials the platform was kept 0.5&nbsp;cm below the water surface, while during retention trials (probe tests) the escape platform was lowered to the bottom of the pool. The light was kept at approximately 60&nbsp;lx during testing. </p>
           <p>Training trials were conducted in two blocks of four on each of the first four days. There was a 3-4&nbsp;hr interval between the blocks on each day. The mice were released into the pool facing the wall at one of four fixed positions around the pool wall in a pseudorandom sequence. The mice were given a maximum of 60&nbsp;s to locate the hidden escape platform. Each mouse performed the four trials in each block consecutively.</p> Whether or not the mice found the platform, they were guided to, or placed on the platform and allowed to sit there during the inter-trial interval (15&nbsp;s). A single retention trial was performed for each mouse on days 5 and 12.
    
           with link to paper and or bibliography
         </div>
       </div>
     </div>
     <div class="panel panel-default">
       <div class="panel-heading">
         <h4 class="panel-title">
           <a data-toggle="collapse" data-parent="#accordionAbstract" href="#collapseStarts">
             Figure: Water maze layout with start positions and platform
           </a>
         </h4>
       </div>
       <div id="collapseStarts" class="panel-collapse collapse">
         <div class="panel-body">
           The start positions for the blocks on days one to four are shown (NW, NE, SW, SE), alongside the start points for the testing on days five and twelve (S).
           <div class="col-xs-12   ">
                   <div class="well">
                           <img src="/articles/watermaze/start.positions.png" class="img-responsive">
                   </div>
           </div>
         </div>
       </div>
     </div>
     <div class="panel panel-default">
       <div class="panel-heading">
         <h4 class="panel-title">
           <a data-toggle="collapse" data-parent="#accordionAbstract" href="#collapseLiterature">
             A brief foray into the literature
           </a>
         </h4>
       </div>
       <div id="collapseLiterature" class="panel-collapse collapse">
         <div class="panel-body">
           <a href="http://dx.doi.org/10.1016/j.bbr.2011.03.007">Statistical analysis of latency outcomes in behavioral experiments</a> from 2011 discusses the analysis of published Barnes maze data in some detail (see 2. Methods). The brief conclusion is that 90% of these analyses are performed incorrectly
         </div>
       </div>
     </div>
    </div>
          
  
  </div> 
</div>

----------------

####Paths for a single mouse
<div class="row">
	<div class="col-md-12">

    <p>Data is most commonly presented as shown in Figure 1A, taking the average latency to platform and using the standard error of the mean as an error bar. This gives apparently clear data, which are then tested for significantly different learning capacity using standard parametric, or occasionally non-parametric methods. (<span class="showtooltip" title="Vorhees C and Williams M (2006). 'Morris Water Maze: Procedures For Assessing Spatial And Related Forms of Learning And Memory.' Nature Protocols, 1, pp. 848-858. ISSN 1754-2189."><a href="http://dx.doi.org/10.1038/nprot.2006.116">Vorhees &amp; Williams, 2006</a></span>) Unfortunately this oversimplifies the data in many ways (not least by incorrectly handling the 60&nbsp;s timepoints where a mouse fails to find the platform) which damage the credibility of the subsequent analysis.</p>

    <p>A look at the raw data in figure 1B tells a different story. The tendency towards shorter latencies over time are still evident here, as seen by the decrease in medians with time, but the homoscedasticity and linear learning progression which are necessary for valid parametric tests, can clearly not be assumed.  </p>

    <p>At this point it is tempting to establish how best to analyse these data, but I will leave that for later and instead address more fundamental questions regarding the latency measure. Although the raw data shown in figure 1B is considerably more detailed than the standard presentation (figure 1A), these times are still an extreme simplification of the spatial data available for each mouse. </p>

    <p>The aim here is to investigate the validity of latency as a measure of learning, to determine the heterogeneity of behaviour and learning within a genotype group and to see whether confounding factors can be identified in the spatial data and used to improve the reliability of learning measures.</p>

    <hr>



    <div class="col-xs-7 col-md-7 pull-right">
      <div class="row">
        <a href="/articles/watermaze/tracks.one.mouse.png" data-toggle="lightbox" data-gallery="multiimages" data-title="Figure 2A: Swimming paths for one mouse during 32 training trials" data-footer="The paths swum by mice in the water maze on four consecutive days during training are shown. They are grouped by starting position and by day, with the paths coloured according to the order they were performed in each day. The position of the platform is shown by a grey circle at (0,100)." class="col-sm-6">
        <img src="/articles/watermaze/tracks.one.mouse.png" class="img-responsive">
        </a>
        <a href="/articles/watermaze/time.one.mouse.png" data-toggle="lightbox" data-gallery="multiimages" data-title="Figure 2B: Swimming paths for one mouse during 32 training trials" data-footer="The paths swum by mice in the water maze on four consecutive days during training are shown. They are grouped by starting position and by day, with the points on the paths coloured according to the swimming time. The position of the platform is shown by a grey circle at (0,100)." class="col-sm-6">
        <img src="/articles/watermaze/time.one.mouse.png" class="img-responsive">
        </a>
      </div>
      <div class="row">
        <a href="/articles/watermaze/speed.one.mouse.png" data-toggle="lightbox" data-gallery="multiimages" data-title="Figure 2C: Swimming paths for one mouse during 32 training trials" data-footer="The paths swum by mice in the water maze on four consecutive days during training are shown. They are grouped by starting position and by day, with the paths coloured according to the instantaneous speed at which the mouse is swimming. The position of the platform is shown by a grey circle at (0,100)." class="col-sm-6">
        <img src="/articles/watermaze/speed.one.mouse.png" class="img-responsive">
        </a>
      </div>
	   <p> <i> Figure 2: Swimming paths during the 32 training trials for a single mouse show the wide range of swimming patterns and swimming speeds which are observed. </i> </p>
    </div>

    <p>An example of the spatial data available for each mouse is shown in figure 2A. Paths are grouped by day and starting position, and coloured according to the sequence of 8 trials each day (block 1 trials 1 to 4 then block 2 trials 1 to 4).</p>

    <p>It is clear that there is a good deal of variability in swimming speed and search strategies, and there is little in figures 2A-C that can be clearly interpreted as learning behaviour, an observation which fits with the heterogeneity observed in figure 1B.  </p>

    <p>What is of interest is to see whether there are any consistent trends in the spatial data. Therefore we begin by looking for patterns in large groups of data.</p>


      
	</div>	
</div>

----------------

####Paths for all mice
<div class="row">
	<div class="col-md-12">

    <div class="col-xs-7 col-md-7 pull-right">
      <div class="row">
        <a href="/articles/watermaze/speed.all.by.genotype.png" data-toggle="lightbox" data-gallery="multiimages" data-title="Figure 3A: Local swimming speeds for each genotype per day" data-footer="The swimming paths for all mice of each genotype on each day are coloured according to swimming speed, giving insights into genotype-specific traits. We see, for example, that genotypes B and F mice in particular tend to avoid the open area of the pool where there is no platform, and genotype D shows a higher number of mice which swim slowly near the edge of the pool." class="col-sm-6">
        <img src="/articles/watermaze/speed.all.by.genotype.png" class="img-responsive">
        </a>
        <a href="/articles/watermaze/speed.all.by.startpoint.png" data-toggle="lightbox" data-gallery="multiimages" data-title="Figure 3B: Local swimming speeds for each genotype according to starting position" data-footer="The swimming paths for all mice of each genotype are coloured according to swimming speed and grouped by starting position. This clearly shows that the mice have a strong tendency to explore the majority of the pool, even when starting from the NE and NW positions which are considerably closer to the platform, although genotype F shows some preference for the area around the platform when starting from a northerly position." class="col-sm-6">
        <img src="/articles/watermaze/speed.all.by.startpoint.png" class="img-responsive">
        </a>
      </div>
      <div class="row">
        <a href="/articles/watermaze/position.all.by.day.png" data-toggle="lightbox" data-gallery="multiimages" data-title="Figure 3C: Positions occupied in the water maze " data-footer="The positions occupied by mice during the day illustrate regions that the mice prefer. The points with a stronger blue colour are occupied for more of the time than paler points, thus the bright blue rim around the edge of the pool for many of the genotypes on day 1 indicates a strong wall-hugging preference for the edge of the pool, rather than carefree exploration. This is very similar behaviour to that which is measured in an open field test and indicates that anxiety contributes significantly to the regions explored. The reduction in wall-hugging over the four days, and the different intensities for each genotype reveal varying anxiety responses and acclimatization rates." class="col-sm-6">
        <img src="/articles/watermaze/position.all.by.day.png" class="img-responsive">
        </a>
        <a href="/articles/watermaze/low.speed.locations.png" data-toggle="lightbox" data-gallery="multiimages" data-title="Figure 3D: Clustered swimming paths for each genotype on each day, showing locations of slow swimming" data-footer="The swimming paths for all mice of each genotype are coloured according to a classification of either fast(pale red) or slow (blue) swimming speed and grouped by day. There is a large difference between genotypes in the preponderance of slow-swimming episodes although slow swimming seems relatively universally to be associated with turning and located predominantly around the edges of the pool." class="col-sm-6">
        <img src="/articles/watermaze/low.speed.locations.png" class="img-responsive">
        </a>
      </div>
	   <p> <i> Figure 3: General tendencies in swimming can be seen by aggregating all of the data from each genotype into specific groups and plotting . </i> </p>
    </div>


    <p>The aim here is to investigate the validity of latency as a measure of learning, to determine the heterogeneity of behaviour and learning within a genotype group and to see whether confounding factors can be identified in the spatial data and used to improve the reliability of learning measures.</p>  
	   
      
      
	</div>	
</div>

----------------

####Discussion and conclusions

----------------

####Methods



<div class="row">
  <div class="col-md-12">
          
    <div class="panel-group" id="accordionMethods">
      <div class="panel panel-default">
        <div class="panel-heading">
          <h4 class="panel-title">
            <a data-toggle="collapse" data-parent="#accordionMethods" href="#collapseStandardImprove">
              Improving standard latency to platform analysis
            </a>
          </h4>
        </div>
        <div id="collapseStandardImprove" class="panel-collapse collapse">
          <div class="panel-body">
            <p>Discussion of problem. </p>
            
          </div>
        </div>
      </div>
      
      <div class="panel panel-default">
        <div class="panel-heading">
          <h4 class="panel-title">
            <a data-toggle="collapse" data-parent="#accordionMethods" href="#collapseother">
              Other
            </a>
          </h4>
        </div>
        <div id="collapseother" class="panel-collapse collapse">
          <div class="panel-body">
            <p>Other. </p>
            
          </div>
        </div>
      </div>
      
    </div>
    
      
  </div> 
</div>



####References
<div class="row">
	<div class="col-md-12">
    <ul>
    <li>Alexander Garthe, Joachim Behr, Gerd Kempermann, Ryan L. Earley,   (2009) Adult-Generated Hippocampal Neurons Allow The Flexible Use of Spatially Precise Learning Strategies.  <em>Plos One</em>  <strong>4</strong>  e5464-NA  <a href="http://dx.doi.org/10.1371/journal.pone.0005464">10.1371/journal.pone.0005464</a></li>
    <li>A. Garthe, Z. Huang, L. Kaczmarek, R. K. Filipkowski, G. Kempermann,   (2014) Not All Water Mazes Are Created Equal: Cyclin d2 Knockout Mice With Constitutively Suppressed Adult Hippocampal Neurogenesis do Show Specific Spatial Learning Deficits.  <em>Genes, Brain And Behavior</em>  <strong>13</strong>  357-364  <a href="http://dx.doi.org/10.1111/gbb.12130">10.1111/gbb.12130</a></li>
    <li>Charles V Vorhees, Michael T Williams,   (2006) Morris Water Maze: Procedures For Assessing Spatial And Related Forms of Learning And Memory.  <em>Nature Protocols</em>  <strong>1</strong>  848-858  <a href="http://dx.doi.org/10.1038/nprot.2006.116">10.1038/nprot.2006.116</a></li>
    </ul>
  </div>
</div>



<a href="https://twitter.com/share" class="twitter-share-button" data-via="A_D_Rowe">Tweet</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+'://platform.twitter.com/widgets.js';fjs.parentNode.insertBefore(js,fjs);}}(document, 'script', 'twitter-wjs');</script>

<div id="disqus_thread"></div>
<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
    var disqus_shortname = 'adroweresearch'; // required: replace example with your forum shortname

    /* * * DON'T EDIT BELOW THIS LINE * * */
    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
<a href="http://disqus.com" class="dsq-brlink">comments powered by <span class="logo-disqus">Disqus</span></a>

Published {{ site.time | date_to_long_string }}

