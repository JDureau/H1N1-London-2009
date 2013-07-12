H1N1-London-2009
================

We illustrate here a generic solution to monitor the transmission rate of a pathogen during an epidemic from incomplete and uncertain 
measures of it spreads among a population. These techniques were introduced in [a recent article][1] written in 
collaboration with [Kostas Kalogeropoulos][2] and [Marc Baguelin][3]. 

The proposed methodology relies on compartmental models in which some parameters are allowed to vary over time
following a diffusion. It then helps to understand what are the underlying and unobserved causes of observed epidemic 
dynamics. We illustrated this approach on a time series of H1N1 cases recorded in London during the 2009 pandemic 
(courtesy of the Health Protection Agency):

The original article relied on the use of the [particle Markov Chain Monte Carlo algorithm][4], and proposed a solution for 
its robust and automatic calibration to facilitate further analog studies on stochastic compartmental models. 

For the sake of transparency, and to foster potential new applications of the proposed methodology, this repository provides
the means to easily reproduce the results presented in the article. It relies on the [library of inference methods][5]
developed in collaboration with Sébastien Ballesteros as part the the [PLOM.IO project][6].


[1]: http://arxiv.org/abs/1203.5950       "Capturing the time-varying drivers of an epidemic using stochastic dynamical systems"
[2]: http://stats.lse.ac.uk/kalogeropoulos/ "Kostas Kalogeropoulos"
[3]: http://www.lshtm.ac.uk/aboutus/people/baguelin.marc "Marc Baguelin"
[4]: http://www.stats.ox.ac.uk/~doucet/andrieu_doucet_holenstein_PMCMC.pdf "Particle Markov Chain Monte Carlo"
[5]: https://github.com/plom-io/plom-pipe "plom-pipe"
[6]: www.plom.io "PLOM.IO"
