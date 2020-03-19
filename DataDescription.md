# Retention time data

# Metadata

## Chromatographic column

column.name
column.usp.code
column.length
column.id	
column.particle.size
column.temperature
column.flowrate


## Eluent composition

### Base solvents

At the current stage only up to 4 solvent channels are available. Practically,
all common cases are covered with ths. If additional solvents are required, they
can be added at any time. Base composition of solvents is recored in volume-%.
Values for all solvents for one eluent should add up to 100%.

The following table summarizes all currently used solvents, their abbrevation
used, as well as the naming of the variable for the eluents A-D.

|name           |abbrev|unit|A              |B              |C              |D              |
|---------------|------|----|---------------|---------------|---------------|---------------|
|water          |h2o   |%   |eluent.A.h2o   |eluent.B.h2o   |eluent.C.h2o   |eluent.D.h2o   |
|methanol       |meoh  |%   |eluent.A.meoh  |eluent.B.meoh  |eluent.C.meoh  |eluent.D.meoh  |
|acetonitrile   |acn   |%   |eluent.A.acn   |eluent.B.acn   |eluent.C.acn   |eluent.D.acn   |
|2-propanol     |iproh |%   |eluent.A.iproh |eluent.B.iproh |eluent.C.iproh |eluent.D.iproh |
|hexane	        |hex   |%	  |eluent.A.hex	  |eluent.B.hex   |eluent.C.hex	  |eluent.D.hex   |
|chloroform	    |chcl3 |%	  |eluent.A.chcl3 |eluent.B.chcl3 |eluent.C.chcl3 |eluent.D.chcl3 |
|dichloromethane|ch2cl2|%	  |eluent.A.ch2cl2|eluent.B.ch2cl2|eluent.C.ch2cl2|eluent.D.ch2cl2|
|heptane        |hept  |%	  |eluent.A.hept  |eluent.B.hept	|eluent.C.hept	|eluent.D.hept  |


### Additives


additives	abbrev	unit	A	B	C	D
formic acid	formic	%	eluent.A.formic	eluent.B.formic	eluent.C.formic	eluent.D.formic
acetic acid	acetic	%	eluent.A.acetic	eluent.B.acetic	eluent.C.acetic	eluent.D.acetic
trifluoroacetic acid	trifluoroacetic	%	eluent.A.trifluoroacetic	eluent.B.trifluoroacetic	eluent.C.trifluoroacetic	eluent.D.trifluoroacetic
phosphoric acid	phosphor	%	eluent.A.phosphor	eluent.B.phosphor	eluent.C.phosphor	eluent.D.phosphor
ammonium acetate	nh4ac	mM	eluent.A.nh4ac	eluent.B.nh4ac	eluent.C.nh4ac	eluent.D.nh4ac
ammonium formiate	nh4form	mM	eluent.A.nh4form	eluent.B.nh4form	eluent.C.nh4form	eluent.D.nh4form
ammonium carbonate	nh4carb	mM	eluent.A.nh4carb	eluent.B.nh4carb	eluent.C.nh4carb	eluent.D.nh4carb
ammonium bicarbonate	nh4bicarb	mM	eluent.A.nh4bicarb	eluent.B.nh4bicarb	eluent.C.nh4bicarb	eluent.D.nh4bicarb
ammonium fluoride	nh4f	mM	eluent.A.nh4f	eluent.B.nh4f	eluent.C.nh4f	eluent.D.nh4f
ammonium hydroxide	nh4oh	mM	eluent.A.nh4oh	eluent.B.nh4oh	eluent.C.nh4oh	eluent.D.nh4oh
triethylamine	trieth	mM	eluent.A.trieth	eluent.B.trieth	eluent.C.trieth	eluent.D.trieth
tripropylamine	triprop	mM	eluent.A.triprop	eluent.B.triprop	eluent.C.triprop	eluent.D.triprop
tributylamine	tribut	mM	eluent.A.tribut	eluent.B.tribut	eluent.C.tribut	eluent.D.tribut
N,N-dimethylhexylamine	nndimethylhex	mM	eluent.A.nndimethylhex	eluent.B.nndimethylhex	eluent.C.nndimethylhex	eluent.D.nndimethylhex

### Gradient

gradient.start.A
gradient.start.B
gradient.start.C
gradient.start.D
gradient.end.A
gradient.end.B
gradient.end.C
gradient.end.D

#### Starting and end conditions

Different ways to prepare solvent and gradients are used. For example eluents 
can be premixed or mixed via the solvent delivery system. A simple example shall
illustrate this:

<i>System 1:</i>

Eluent A: 100% H2O + 0.1% formic acid

Eluten B: 100% ACN + 0.1% formic acid

The gradient starts from 95% A and 5% B and is increased linear to 5% A and 95%
B in 10 minutes

<i>System 2:</i>

Eluent A: 95% H2O / 5% ACN + 0.1% formic acid

Eluten B: 5% H2O / 95% ACN + 0.1% formic acid

The gradient starts from 100% A and 0% B and is increased linear to 0% A and 100%
B in 10 minutes.

The difference between the two systems is that the second system uses premixed 
eluents, while the first system uses the solvent delivery system to mimic the
same mixing. However, nominally the two systems deliver the same gradient.

Using the metadata notation so far would flag them as two different systems for
prediction of retention times. To overcome this issue the "true" gradient starting
and ending conditions are calculated based on the solvent composition of the
different eluents and the gradient conditions.

|solvent        |abrev |unit|gradient start       |gradient end       |
|---------------|------|----|---------------------|-------------------|
|water          |h2o   |%   |gradient.start.h2o   |gradient.end.h2o   |
|methanol       |meoh  |%   |gradient.start.meoh  |gradient.end.meoh  |
|acetonitrile   |acn   |%   |gradient.start.acn   |gradient.end.acn   |
|2-propanol     |iproh |%   |gradient.start.iproh |gradient.end.iproh |
|hexane	        |hex   |%	  |gradient.start.hex   |gradient.end.hex   |
|chloroform	    |chcl3 |%	  |gradient.start.chcl3 |gradient.end.chcl3 |
|dichloromethane|ch2cl2|%	  |gradient.start.ch2cl2|gradient.end.ch2cl2|
|heptane        |hept  |%	  |gradient.start.hept  |gradient.end.hept  |