## Work done during GSoC
To see all the work done suring the 2019 GSoC coding period, see this 
[PR list](https://github.com/arviz-devs/arviz/pulls?page=1&q=is%3Apr+author%3AOriolAbril+archived%3Afalse+label%3AGSOC&utf8=%E2%9C%93).
This list contains all my contributions during GSoC coding period. Below, these PRs are divided by topics and the most important contributions in each topic are summarized.

---
### Information Criteria

Information criteria allow to evaluate the predictive accuracy of a model. In some cases, this quantity is so 
relevant to the analysis that it can be used to compare 
different models and choose the one with the better predictive accuracy. ArviZ has some functions designed to calculate 
different information criteria (`az.loo` and `az.waic`) and to analyze its results (`az.compare`, `az.plot_compare`, 
`az.plot_elpd` and `az.plot_khat`). During GSoC, I have modified these functions in order to extend them and ease 
their interpretation:

* I created a new class `az.ELPDData` designed to store and print in an informative manner the results of information
criteria. 
* I modified the computation of information criteria to use internally `az.wrap_xarray_ufunc`. This allows 3 key improvements.
The first is that there is no longer the need to convert to unlabeled data, therefore pointwise information criteria 
results are labeled like the rest of the data in InferenceData objects which eases the identification of problematic
observations. The second is that working with multidimensional data is automatically handled by xarray and the shape of 
the original object is kept. And the third is that this change allows easy parallelization of the calculations using 
dask via xarray. 
* This previous change also defines by convenience ArviZ's default shapes and dimension names. InferenceData objects 
generally contain first the `chain` dimension followed by the `draw` dimension and then any number of dimensions depending
on the variable shape. In some cases, we want to combine all chains into a single array; in ArviZ this should be 
done with xarray's `stack(sample=("chain", "draw"))`. This combines the `chain` and the `draw` dimension to a single 
dimension called `sample` which is placed as the last dimension, leaving an object with first the variable shape and then 
the `sample` shape. 
* I created the `az.plot_elpd` in order to compare pointwise information criteria values of several models, with 
coloring based on label values and non-degenerate pairwise plots to compare more than two models at once.
* I added many customization options to `az.plot_khat` like coloring based on labels, a summary of the quality of khat 
values and showing the labels of each observation when hovering over. 
* I created a context manager `az.interactive_backend` to allow temporal change of matplotlib backend between the ususal inline backend used in jupyter notebooks, jupyter lab or spyder and any of the supported interactive backends.
* I also extended the tests of information criteria functions to have their behaviour checked on multidimensional objects (`chain`, `draw` and at least 2 more dimensions).
* I have also started working on sampling wrappers in order to allow ArviZ to refit the same model on different sets of data.
As ArviZ has no sampling capabilities and it is backend agnostic, this wrappers allow it to perform refits and to do them 
using any backend available like PyStan or emcee. At the time of writing, working sampling wrappers for PyStan and emcee 
have been already written. PyMC3 wrappers cannot work yet until this [PyMC3 issue](https://github.com/pymc-devs/pymc3/issues/3007) is fixed. The PR implementing this is still unmerged as it also depends on the changes on InferenceData scheme.
* In parallel to the sampling wrappers, I have also written a port to ArviZ of the reloo function of the brms R package. 
This function uses the sampling wrappers to calculate exact cross validation values for problematic observations where 
numerical approximations do not work. After GSoC, I also plan on implementing a numerical approximation of the 
leave-future-out cross validation that also needs to perform some refits of the model.


#### PRs in this caterory
* [#678](https://github.com/arviz-devs/arviz/pull/678): +809 −102
* [#700](https://github.com/arviz-devs/arviz/pull/700): +319 −38
* [#701](https://github.com/arviz-devs/arviz/pull/701) (bugfix for #678): +8 −13
* [#727](https://github.com/arviz-devs/arviz/pull/727): +118 −8
* [#748](https://github.com/arviz-devs/arviz/pull/748) (bugfix for #678): +3 −2
* [#755](https://github.com/arviz-devs/arviz/pull/755): +224 −143
* [#764](https://github.com/arviz-devs/arviz/pull/764): +6 −0
* [#771](https://github.com/arviz-devs/arviz/pull/771) [UNMERGED]: +844 −0
* [#790](https://github.com/arviz-devs/arviz/pull/790) (fix for #678): +24 −24

Total lines of code added/removed from ArviZ for this section: +2356 -330

---
### Convergence Assessment

#### PRs in this caterory
* [#708](https://github.com/arviz-devs/arviz/pull/708): +405 −0
* [#724](https://github.com/arviz-devs/arviz/pull/724): +397 −37
* [#778](https://github.com/arviz-devs/arviz/pull/778) (bugfix for both #708 and #724): +4 −2

Total lines of code added/removed from ArviZ for this section: +806 -39

---
### Model Checking

#### PRs in this caterory
* [#696](https://github.com/arviz-devs/arviz/pull/696): +837 −24
* [#738](https://github.com/arviz-devs/arviz/pull/738) (documentation bugfix for #696): +2 −2
* [#781](https://github.com/arviz-devs/arviz/pull/781): +52 −4

Total lines of code added/removed from ArviZ for this section: +891 -30

---
### InferenceData scheme modifications

#### PRs in this caterory
* [#702](https://github.com/arviz-devs/arviz/pull/702): +70 −17
* [#715](https://github.com/arviz-devs/arviz/pull/715): +24 −19
* [#720](https://github.com/arviz-devs/arviz/pull/720) (bugfix for #715): +2 −4
* [#739](https://github.com/arviz-devs/arviz/pull/739): +101 −9
* [#794](https://github.com/arviz-devs/arviz/pull/794) [UNMERGED]: +533 −291

Total lines of code added/removed from ArviZ for this section: +730 -340

---
### Global parameters

#### PRs in this caterory
* [#734](https://github.com/arviz-devs/arviz/pull/734): +374 −20
* [#787](https://github.com/arviz-devs/arviz/pull/787): +208 −37

Total lines of code added/removed from ArviZ for this section: +582 -57

---

### Other PRs

* [#714](https://github.com/arviz-devs/arviz/pull/714): +1 −1
* [#723](https://github.com/arviz-devs/arviz/pull/723): +72 −17
* [#730](https://github.com/arviz-devs/arviz/pull/730): +25 −15
* [#736](https://github.com/arviz-devs/arviz/pull/736): +4 −3
* [#765](https://github.com/arviz-devs/arviz/pull/765): +76 −28
* [#768](https://github.com/arviz-devs/arviz/pull/768): +3 −1
* [#769](https://github.com/arviz-devs/arviz/pull/769): +4 −1 
* [#773](https://github.com/arviz-devs/arviz/pull/773): +63 −28
* [#776](https://github.com/arviz-devs/arviz/pull/776): +0 −1
* [#779](https://github.com/arviz-devs/arviz/pull/779): +15 −1
* [#788](https://github.com/arviz-devs/arviz/pull/788) [UNMERGED]: +3 −2

Total lines of code added/removed from ArviZ for this section: +266 -98


