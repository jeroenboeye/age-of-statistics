<template>
  <h2>Methods</h2>
  <hr>
  <h3>Confidence Intervals and why they are Important</h3>

  <p>
    A common critique you will hear when talking about any statistic is "you can't trust that value,
    the sample size is too small!". A natural question is then "well how big should the sample size
    be?" or the equivalent question of "how much should I trust this statistic given the sample size".
    This is where confidence intervals come in.
    
    A key thing to realise is that when we create statistics, like win rates, what we are creating
    are estimates of some true unknown value. Confidence intervals can thus be thought of as the range
    of values in which the true value is likely to be found in i.e. there is a 95% chance that the
    true value for the win rate exists within this band. Throughout these documents the 95% confidence
    intervals are presented as error bars around the point estimates. More generally speaking, the
    wider the confidence interval is the less trust we should have in the estimate whilst the narrower
    the confidence interval is the more trust we should have in the estimate.
        
    Please note that my above description of confidence intervals isn't technically correct in that
    if you repeated it to a statistician they will probably roll their eyes at you or lecture you.
    That being said it is good enough to give an intuitive sense of what confidence intervals
    represent and how to interpret them. If you want a more accurate description please see
    <a 
      href="https://www.census.gov/programs-surveys/saipe/guidance/confidence-intervals.html"
    >here</a>.
  </p>

  <h3>Naive Win Rates</h3>
    
  <p>
    Whenever something is indicated as being a "Naive win rate" it means that it has been calculated
    by fitting a logistic regression model to each civ's match data independently, i.e.:
        
    $$
    \displaylines{
    Y_{ij} \sim Bin(1, p_{ij}) \\
    p_{ij} = \text{logistic}(\beta_i +  \beta_d d_{j})
    }
    $$
        
    Where:
        
    <ul>
      <li>\(Y_{ij}\) is 1 if civilisation \(i\) won its \(j\)'th match</li>
      <li>\(\beta_i\) is civilisation \(i\)'s logit win rate</li>
      <li>\(d_j\) is the difference in mean Elo between team 1 and team 2 in match \(j\)</li>
      <li>\(\beta_d\) is the importance of the difference in mean Elo between team 1 and team 2 in match \(j\)</li>
    </ul>
        
    All mirror matchups are excluded.
        
    It is referred to as the "naive win rate" as it doesn't take into account the civilisation play
    rates and thus more represents the civilisations win rate against the most played civilisations.
  </p>
    


  <h3>Averaged Win Rates</h3>

  <p>
    Averaged win rates are calculated by taking the average across all civilisation v civilisation win
    rates. I.e The Aztec win rate is calculated by taking the mean of their win rate vs Berbers,
    Britons, Bulgarians, etc, separately. This statistic can be thought of as the win rate if your
    opponent was picking their civilisation at random.

    For 1v1's each civilisation v civilisation win rate is calculated using the "naive" method
    mentioned above. For team games though the win rates are calculated by fitting a logistic
    regression that derives the probability of winning as the average across each pairwise
    civilisation match-up.  For example, let's say in match \(j\) that team 1 had civilisations A, B
    and C whilst team 2 had civilisations X, Y and Z. The model fitted would then be:

    $$
    \displaylines{
    Y_{j} \sim Bin(1, p_{j}) \\
    p_j = \text{logistic}
    \left(\frac{
    \beta_{AX} + \beta_{AY} + \beta_{AZ} + 
    \beta_{BX} + \beta_{BY} + \beta_{BZ} + 
    \beta_{CX} + \beta_{CY} + \beta_{CZ}
    }{9} +  \beta_d d_{j}\right)
    }
    $$

    Where:

    <ul>
      <li>\(Y_j\) = 1 if team 1 won or 0 if team 2 won</li>
      <li>\(\beta_{mn}\) is civilisation \(m\)'s win rate against civilisation \(n\)</li>
      <li>\(d_j\) is the difference in mean Elo between team 1 and team 2</li>
      <li>\(\beta_d\) is the importance of the difference in mean Elo between team 1 and team 2 in match \(j\)</li>
    </ul>

    Please note that a major limitation of this formulation is that it doesn't allow for any
    interaction effects. I.e. it doesn't account for the fact that some civilisation pairings
    are stronger together than if they were to be considered independently (think a team of all
    cavalry civilisation vs a team of both archer and cavalry civilisation).
    
    In all cases, a small Laplace smoother was added to avoid issues associated with certainty
    bias from low civilisation v civilisation sample sizes (most notably in the Empire Wars data).
    This will mean that the confidence intervals are very marginally underestimated and biased
    towards 50%; realistically however this should be negligible.
  </p>

  <h3>Removing Single Civilisation Players</h3>

  <p>
    In some cohorts "single civilisation pickers" have been removed. In these cohorts
    single civilisation players are identified as those who have a played at least 10 games
    and who have a playrate of 	&#62;40% for any single civilisation. In these cases all matches
    where that player participated are removed.
  </p>
</template>

<script>
export default {
    mounted() {
        if(window.MathJax){
            window.MathJax.typeset()
        }
    }
}
</script>
