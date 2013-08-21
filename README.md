H1N1-London-2009
================

We illustrate here a generic solution to monitor the transmission rate of a pathogen during an epidemic from incomplete and uncertain 
measures of it spreads among a population. These techniques were introduced in [a recent article][1] written in 
collaboration with [Kostas Kalogeropoulos][2] and [Marc Baguelin][3]. 

The proposed methodology relies on compartmental models in which some parameters are allowed to vary over time
following a [diffusion][8]. It then helps to understand what are the underlying and unobserved causes of observed epidemic 
dynamics. We illustrated this approach on a time series of H1N1 cases recorded in London during the 2009 pandemic 
(courtesy of the Health Protection Agency):

![data](https://raw.github.com/JDureau/H1N1-London-2009/master/images/data.png?login=JDureau&token=c5b1e3d648591265b128978f10a0bcee)

The unusual shape of the epidemic trajectory, exhibiting two peaks, reflects variations of extrinsic quantities
that drive its evolution. Holidays, and their subsequent impact on the frequency at which people meet and infect 
each other, provide a natural explanation to the decline of the first wave. However, the additional role of climate
on the transmissibility of influenza is also debated, and media have played an important role on individual
awareness and behaviour. We show that according to the model we use, the effective transmission rate of H1N1 evolved 
in the following way:

![data](https://raw.github.com/JDureau/H1N1-London-2009/master/images/beta.png?login=JDureau&token=908ed37544cffb2e67155b264bde06ba)

This result confirms that holidays have been the main driver of the epidemic (they're indicated by darker grey areas), and further quantifies their impact
on the transmission rate of influenza. For example, it shows that the impact of summer holidays is about twice more 
important than fall holidays, providing an indication on the potential impact of closing schools as a mean to 
mitigate an epidemic.

The original article relied on the use of the [particle Markov Chain Monte Carlo algorithm][4], and proposed a solution for 
its robust and automatic calibration to facilitate further analog studies on stochastic compartmental models. 

For the sake of transparency, and to foster potential new applications of the proposed methodology, this repository provides
the means to easily reproduce the results presented in the article. It relies on the [library of inference methods][5]
developed in collaboration with Sébastien Ballesteros as part the the [PLOM.IO project][6].

Reproducing the results:
------------------------

Data is contained in the data folder, in the csv format. Additionally, the folder SEIR_beta_t contains json files that 
define a model and link it to the data, following the [PLOM.IO grammar][6]. To generate the code and play with the model
yourself, simply [install the package][7], and compile the model with:

    plom build -t map.json --local

The joint posterior density of paths and parameters can be explored with the following command (run in the /model folder):

    plom pipe theta.json | ./pmcmc psr --full -M 10000 -a 0.98 -N 8 -J 1000
    
The latter takes a bit less than 20 minutes using the 8 cores of my laptop (the number of cores is determined by the N option).




[1]: http://arxiv.org/abs/1203.5950       "Capturing the time-varying drivers of an epidemic using stochastic dynamical systems"
[2]: http://stats.lse.ac.uk/kalogeropoulos/ "Kostas Kalogeropoulos"
[3]: http://www.lshtm.ac.uk/aboutus/people/baguelin.marc "Marc Baguelin"
[4]: http://www.stats.ox.ac.uk/~doucet/andrieu_doucet_holenstein_PMCMC.pdf "Particle Markov Chain Monte Carlo"
[5]: https://github.com/plom-io/plom-pipe "plom-pipe"
[6]: http://plom.io/cli/grammar "PLOM.IO grammar"
[7]: http://plom.io/cli "workflow"
[8]: http://en.wikipedia.org/wiki/Diffusion_process "Diffusions"

