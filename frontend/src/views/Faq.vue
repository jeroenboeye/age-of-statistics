<template>
  <h2>Frequently Asked Questions</h2>
 
  <hr>
  <ul>
    <p class="faq-q">
      Why have you included games with players below an Elo of X?
    </p>
  </ul>
  <p class="faq-a">
    Using Elo as a filter for which matches to include when generating the statistics ultimately 
    results in a tradeoff. Lowering the Elo threshold means that the statistics better represent
    the player base but at the expense of them less representing the civilisation's performance
    when "played-correctly". Where to place the cut-off is thus fundamentally subjective, for
    example does it matter what the civilisations performance at the pro level is if this isn't
    reflective of the civilisations performance at your skill level?
    <br><br>
    The statistics presented on this site were generated under the belief that balance should be
    considered at all levels of play. As an example for why this matters think about quick-walling; 
    many players, particularly at the lower Elos, simply don't (and never will) have the dexterity 
    or reaction speeds to properly quick-wall. So should it be considered balanced if you had an 
    OP unit that could be effectively countered by quick-walling even though a large
    chunk of the playerbase can't do this and would therefore have no way of dealing with this
    imbalance?
    <br><br>
    This site therefore focuses on the top ~25% of the player base (&#62; 1200 Elo in 1v1s) which
    it is felt provides a suitable balance between civilisations being "played correctly" whilst
    still representing a decent proportion of the player base.
  </p>
  <hr>
  <ul>
    <p class="faq-q">
      Are these statistics actually representative for non-meta civilisations as most people
      just play meta?
    </p>
  </ul>
  <p class="faq-a">
    Maybe? This fundamentally comes down to what you are wanting to estimate, the (hypothetical) 
    win rate based on the civ the being "played-correctly" or the win rate based upon
    how players actually play the game. The statistics on this site will be an estimate
    of the latter.
    <br><br>
    How to interpret these statistics is potentially then more subjective as abnormally
    high/low win rates could be due to the civilisation not being "played-correctly" as opposed to
    them being genuinely under/overpowered. 
    That being said, the observed win rates presented on this site should provide an insight into
    how people are actually experiencing the game. For example does it matter that a civilisation
    is hypothetically balanced when "played-correctly" if the vast majority of the people playing
    the game are experiencing imbalance with them?
  </p>
  <hr>
    
  <ul>
    <p class="faq-q">
      Do these statistics mean that civilisation X needs to be nerfed/buffed? 
    </p>
  </ul>

  <p class="faq-a">
    Again maybe? Win rates can help to identify potential problem areas however their use beyond this
    is extremely limited; in particular they don't give any reason as to why a problem exists or 
    even if problem does truly exist at all (the underlying data is very prone to bias due to
    its observational nature). Because of this, win rates should never be the
    sole justification for a balance change; instead they should be combined with
    expert opinion, scenario analysis & comparisons to the intended game design in order
    to justify and make informed proposals.
  </p>
  <hr>
  <ul>
    <p class="faq-q">
      Have you accounted for players who always pick the same civilisation?
    </p>
  </ul>

  <p class="faq-a">
    For those who may not be aware, pick rates have a large impact on observed win rates. To
    get an idea of the magnitude of this impact please see this 
    <a 
      href="https://www.reddit.com/r/aoe2/comments/pl4jpz/a_brief_look_at_the_impact_of_civ_picking_on_win/"
    >reddit post</a>.
    
    Though to summarise, the main impacts appear to be:
    <ul>
      <li>
        overplayed civilisations have their win rates biased towards 50%
      </li>
      <li>
        underplayed civilisations have their win rates biased towards their win rate vs
        the most overplayed civilisations
      </li>
    </ul>
    It must be noted however that this doesn't take into account biases associated with the
    "familiarity" of playing a specific civilisation more. That being said, to try and account
    for this two additional cohorts have been created in which all players who have a play rate
    of &#62; 40% for their most played civilisation are removed. It must be stressed
    that this is at best a partial solution to what is a very difficult problem to solve.
  </p>
</template>


<style scoped>
.faq-a {
    margin-bottom: 2.5rem;
}

.faq-q {
    font-weight: 700;
    margin-top: 2.5rem;
}
</style>