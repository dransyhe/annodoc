---
layout: entry
title: Annodoc annotation documentation support system
---

1. My aunt's can opener can open a drum.  

- Gold standard: 

~~~ conllu
# this is one sentence
1	My	my	PRP$	PRP$	_	2	nmod:poss	_	_
2	aunt	aunt	NN	NN	_	7	nsubj	_	_
3	's	's	POS	POS	_	5	case	_	_
4	can	can	NN	NN	_	5	compound	_	_
5	opener	opener	NN	NN	_	2	nmod:poss	_	_
6	can	can	MD	MD	_	7	aux	_	_
7	open	open	VB	VB	_	0	root	_	_
8	a	a	DT	DT	_	9	det	_	_
9	drum	drum	NN	NN	_	7	obj	_	_
10	.	.	.	.	_	7	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
My/PRP$ aunt/NN 's/POS can/NN opener/NN can/MD open/VB a/DT drum/NN ./.
nmod:poss(aunt-2, My-1)
nmod:poss(opener-5, aunt-2)
case(aunt-2, 's-3)
compound(opener-5, can-4)
nsubj(open-7, opener-5)
aux(open-7, can-6)
root(ROOT-0, open-7)
det(drum-9, a-8)
obj(open-7, drum-9)
~~~

- NN-based dependency parser:

~~~ sdparse
My/PRP$, aunt/NN, 's/POS, can/MD, opener/NN, can/MD, open/VB, a/DT, drum/NN, ./.
nmod:poss(aunt-2, My-1)
nmod:poss(opener-5, aunt-2)
case(aunt-2, 's-3)
aux(opener-5, can-4)
nsubj(open-7, opener-5)
aux(open-7, can-6)
root(ROOT-0, open-7)
det(drum-9, a-8)
obj(open-7, drum-9)
punct(open-7, .-10)
~~~

2. The old car broke down in the car park.  

- Gold standard: 

~~~ conllu
# this is one sentence
1	The	the	DT	DT	_	3	det	_	_
2	old	old	JJ	JJ	_	3	amod	_	_
3	car	car	NN	NN	_	4	nsubj	_	_
4	broke	break	VBD	VBD	_	0	root	_	_
5	down	down	RP	RP	_	4	dep	_	_
6	in	in	IN	IN	_	9	case	_	_
7	the	the	DT	DT	_	9	det	_	_
8	car	car	NN	NN	_	9	compound	_	_
9	park	park	NN	NN	_	4	obl	_	_
10	.	.	.	.	_	4	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
The/DT old/JJ car/NN broke/VBD down/RP in/IN the/DT car/NN park/NN ./.
det(car-3, The-1)
amod(car-3, old-2)
nsubj(broke-4, car-3)
root(ROOT-0, broke-4)
compound:prt(broke-4, down-5)
case(park-9, in-6)
det(park-9, the-7)
compound(park-9, car-8)
obl:in(broke-4, park-9)
~~~

- NN-based dependency parser:

~~~ sdparse
The/DT, old/JJ, car/NN, broke/VBD, down/RP, in/IN, the/DT, car/NN, park/NN, ./.
det(car-3, The-1)
amod(car-3, old-2)
nsubj(broke-4, car-3)
root(ROOT-0, broke-4)
compound:prt(broke-4, down-5)
case(park-9, in-6)
det(park-9, the-7)
compound(park-9, car-8)
obl(broke-4, park-9)
punct(broke-4, .-10)
~~~

3. At least two men broke in and stole my TV.  

- Gold standard: 

~~~ conllu
# this is one sentence
1	At	at	RB	RB	_	2	advmod	_	_
2	least	least	RBS	RBS	_	4	advmod	_	_
3	two	two	CD	CD	_	2	dep	_	_
4	men	man	NNS	NNS	_	5	nsubj	_	_
5	broke	break	VBD	VBD	_	0	root	_	_
6	in	in	RP	RP	_	5	dep	_	_
7	and	and	CC	CC	_	5	cc	_	_
8	stole	steal	VBD	VBD	_	7	dep	_	_
9	my	my	PRP$	PRP$	_	10	nmod:poss	_	_
10	tv	tv	NN	NN	_	8	obj	_	_
11	.	.	.	.	_	5	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
At/IN least/JJS two/CD men/NNS broke/VBD in/RP and/CC stole/VBD my/PRP$ TV/NN ./.
case(least-2, At-1)
obl:npmod(two-3, least-2)
nummod(men-4, two-3)
nsubj(broke-5, men-4)
nsubj(stole-8, men-4)
root(ROOT-0, broke-5)
compound:prt(broke-5, in-6)
cc(stole-8, and-7)
conj:and(broke-5, stole-8)
nmod:poss(TV-10, my-9)
obj(stole-8, TV-10)
~~~

- NN-based dependency parser:

~~~ sdparse
At/RB, least/RBS, two/CD, men/NNS, broke/VBD, in/IN, and/CC, stole/VBD, my/PRP$, TV/NN, ./.
case(least-2, At-1)
obl:npmod(two-3, least-2)
nummod(men-4, two-3)
nsubj(broke-5, men-4)
root(ROOT-0, broke-5)
compound:prt(broke-5, in-6)
cc(stole-8, and-7)
conj(broke-5, stole-8)
nmod:poss(TV-10, my-9)
obj(stole-8, TV-10)
punct(broke-5, .-11)
~~~

4. Kim and Sandy both broke up with their partners.  

- Gold standard: 

~~~ conllu
# this is one sentence
1	Kim	Kim	NNP	NNP	_	5	nsubj	_	_
2	and	and	CC	CC	_	1	cc	_	_
3	Sandy	Sandy	NNP	NNP	_	2	dep	_	_
4	both	both	RB	RB	_	5	advmod	_	_
5	broke	break	VBD	VBD	_	0	root	_	_
6	up	up	RP	RP	_	5	dep	_	_
7	with	with	IN	IN	_	9	case	_	_
8	their	they	PRP$	PRP$	_	9	nmod:poss	_	_
9	partners	partner	NNS	NNS	_	5	obl	_	_
10	.	.	.	.	_	5	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
Kim/NNP and/CC Sandy/NNP both/DT broke/VBD up/RP with/IN their/PRP$ partners/NNS ./.
nsubj(broke-5, Kim-1)
cc(Sandy-3, and-2)
conj:and(Kim-1, Sandy-3)
nsubj(broke-5, Sandy-3)
dep(broke-5, both-4)
root(ROOT-0, broke-5)
compound:prt(broke-5, up-6)
case(partners-9, with-7)
nmod:poss(partners-9, their-8)
obl:with(broke-5, partners-9)
~~~

- NN-based dependency parser:

~~~ sdparse
Kim/NNP, and/CC, Sandy/NNP, both/CC, broke/VBD, up/RP, with/IN, their/PRP$, partners/NNS, ./.
nsubj(broke-5, Kim-1)
cc(Sandy-3, and-2)
conj(Kim-1, Sandy-3)
dep(Kim-1, both-4)
root(ROOT-0, broke-5)
compound:prt(broke-5, up-6)
case(partners-9, with-7)
nmod:poss(partners-9, their-8)
obl(broke-5, partners-9)
punct(broke-5, .-10)
~~~


5. The horse as well as the rabbits which we wanted to eat has escaped.  

- Gold standard: 

~~~ conllu
# this is one sentence
1	The	the	DT	DT	_	2	det	_	_
2	horse	horse	NN	NN	_	14	nsubj	_	_
3	as	as	RB	RB	_	4	advmod	_	_
4	well	well	RB	RB	_	7	dep	_	_
5	as	as	RB	RB	_	4	advmod	_	_
6	the	the	DT	DT	_	7	det	_	_
7	rabbits	rabbit	NNS	NNS	_	2	cc	_	_
8	which	which	WDT	WDT	_	10	dep	_	_
9	we	we	PRP	PRP	_	10	dep	_	_
10	wanted	want	VBD	VBD	_	7	dep	_	_
11	to	to	TO	TO	_	10	xcomp	_	_
12	eat	eat	VB	VB	_	11	dep	_	_
13	has	have	VBZ	VBZ	_	14	aux	_	_
14	escaped	escape	VBN	VBN	_	0	root	_	_
15	.	.	.	.	_	14	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
The/DT horse/NN as/RB well/RB as/IN the/DT rabbits/NNS which/WDT we/PRP wanted/VBD to/TO eat/VB has/VBZ escaped/VBN ./.
det(horse-2, The-1)
nsubj(escaped-14, horse-2)
cc(rabbits-7, as-3)
fixed(as-3, well-4)
fixed(as-3, as-5)
det(rabbits-7, the-6)
conj:and(horse-2, rabbits-7)
obj(wanted-10, rabbits-7)
nsubj:xsubj(eat-12, rabbits-7)
nsubj(escaped-14, rabbits-7)
ref(rabbits-7, which-8)
nsubj(wanted-10, we-9)
acl:relcl(rabbits-7, wanted-10)
mark(eat-12, to-11)
xcomp(wanted-10, eat-12)
aux(escaped-14, has-13)
root(ROOT-0, escaped-14)
~~~

- NN-based dependency parser:

~~~ sdparse
The/DT, horse/NN, as/RB, well/RB, as/IN, the/DT, rabbits/NNS, which/WDT, we/PRP, wanted/VBD, to/TO, eat/VB, has/VBZ, escaped/VBN, ./.
det(horse-2, The-1)
nsubj(escaped-14, horse-2)
cc(rabbits-7, as-3)
fixed(as-3, well-4)
fixed(as-3, as-5)
det(rabbits-7, the-6)
conj(horse-2, rabbits-7)
obj(wanted-10, which-8)
nsubj(wanted-10, we-9)
acl:relcl(rabbits-7, wanted-10)
mark(eat-12, to-11)
xcomp(wanted-10, eat-12)
aux(escaped-14, has-13)
root(ROOT-0, escaped-14)
punct(escaped-14, .-15)
~~~

6. It was my aunt's car which we sold at auction last year in February.  

- Gold standard: 

~~~ conllu
# this is one sentence
1	It	it	PRP	PRP	_	4	nsubj	_	_
2	was	be	VBD	VBD	_	4	cop	_	_
3	my	my	PRP$	PRP$	_	4	nmod:poss	_	_
4	aunt	aunt	NN	NN	_	0	root	_	_
5	's	's	POS	POS	_	6	case	_	_
6	car	car	NN	NN	_	4	nmod:poss	_	_
7	which	which	WDT	WDT	_	9	dep	_	_
8	we	we	PRP	PRP	_	9	nsubj	_	_
9	sold	sell	VBD	VBD	_	4	dep	_	_
10	at	at	IN	IN	_	11	case	_	_
11	auction	auction	NN	NN	_	9	obl	_	_
12	last	last	RB	RB	_	9	advmod	_	_
13	year	year	NN	NN	_	12	obl:npmod	_	_
14	in	in	IN	IN	_	15	case	_	_
15	February	February	NNP	NNP	_	9	obl	_	_
16	.	.	.	.	_	4	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
It/PRP was/VBD my/PRP$ aunt/NN 's/POS car/NN which/WDT we/PRP sold/VBD at/IN auction/NN last/JJ year/NN in/IN February/NNP ./.
nsubj(car-6, It-1)
cop(car-6, was-2)
nmod:poss(aunt-4, my-3)
nmod:poss(car-6, aunt-4)
case(aunt-4, 's-5)
root(ROOT-0, car-6)
obj(sold-9, car-6)
ref(car-6, which-7)
nsubj(sold-9, we-8)
acl:relcl(car-6, sold-9)
case(auction-11, at-10)
obl:at(sold-9, auction-11)
amod(year-13, last-12)
obl:tmod(sold-9, year-13)
case(February-15, in-14)
obl:in(sold-9, February-15)
~~~

- NN-based dependency parser:

~~~ sdparse
It/PRP, was/VBD, my/PRP$, aunt/NN, 's/POS, car/NN, which/WDT, we/PRP, sold/VBD, at/IN, auction/NN, last/JJ, year/NN, in/IN, February/NNP, ./.
nsubj(car-6, It-1)
cop(car-6, was-2)
nmod:poss(aunt-4, my-3)
nmod:poss(car-6, aunt-4)
case(aunt-4, 's-5)
root(ROOT-0, car-6)
obj(sold-9, which-7)
nsubj(sold-9, we-8)
acl:relcl(car-6, sold-9)
case(auction-11, at-10)
obl(sold-9, auction-11)
amod(year-13, last-12)
obl:tmod(sold-9, year-13)
case(February-15, in-14)
obl(sold-9, February-15)
punct(car-6, .-16)
~~~

7. Natural disasters – storms, flooding, hurricanes – occur infrequently but cause devastation that strains resources to breaking point.  

- Gold standard: 

~~~ conllu
# this is one sentence
1	Natural	natural	JJ	JJ	_	2	amod	_	_
2	disasters	disaster	NNS	NNS	_	10	nsubj	_	_
3	–	–	:	:	_	4	punct	_	_
4	storms	storm	NNS	NNS	_	2	dep	_	_
5	,	,	,	,	_	6	punct	_	_
6	flooding	flooding	NN	NN	_	4	dep	_	_
7	,	,	,	,	_	8	punct	_	_
8	hurricanes	hurricane	NNS	NNS	_	4	dep	_	_
9	–	–	:	:	_	4	punct	_	_
10	occur	occur	VBP	VBP	_	0	root	_	_
11	infrequently	infrequently	RB	RB	_	10	advmod	_	_
12	but	but	CC	CC	_	10	cc	_	_
13	cause	cause	VBP	VBP	_	12	dep	_	_
14	devastation	devastation	NN	NN	_	13	obj	_	_
15	that	that	WDT	WDT	_	16	dep	_	_
16	strains	strain	VBZ	VBZ	_	14	dep	_	_
17	resources	resource	NNS	NNS	_	16	obj	_	_
18	to	to	IN	IN	_	20	case	_	_
19	breaking	breaking	NN	NN	_	20	compound	_	_
20	point	point	NN	NN	_	16	obl	_	_
21	.	.	.	.	_	10	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
Natural/JJ disasters/NNS –/SYM storms/NNS ,/, flooding/NN ,/, hurricanes/NNS –/: occur/VB infrequently/RB but/CC cause/VB devastation/NN that/WDT strains/VBZ resources/NNS to/IN breaking/VBG point/NN ./.
amod(disasters-2, Natural-1)
root(ROOT-0, disasters-2)
dep(storms-4, –-3)
nmod(disasters-2, storms-4)
appos(disasters-2, flooding-6)
appos(disasters-2, hurricanes-8)
dep(disasters-2, occur-10)
advmod(occur-10, infrequently-11)
cc(cause-13, but-12)
dep(disasters-2, cause-13)
conj:but(occur-10, cause-13)
obj(cause-13, devastation-14)
nsubj(strains-16, devastation-14)
ref(devastation-14, that-15)
acl:relcl(devastation-14, strains-16)
obj(strains-16, resources-17)
mark(breaking-19, to-18)
advcl(strains-16, breaking-19)
obj(breaking-19, point-20)
~~~

- NN-based dependency parser:

~~~ sdparse
Natural/JJ, disasters/NNS, –/SYM, storms/NNS, ,/,, flooding/NN, ,/,, hurricanes/NNS, –/SYM, occur/VBP, infrequently/RB, but/CC, cause/VB, devastation/NN, that/IN, strains/NNS, resources/NNS, to/IN, breaking/VBG, point/NN, ./.
amod(disasters-2, Natural-1)
compound(storms-4, disasters-2)
dep(storms-4, –-3)
root(ROOT-0, storms-4)
punct(storms-4, ,-5)
conj(storms-4, flooding-6)
punct(storms-4, ,-7)
conj(storms-4, hurricanes-8)
dep(occur-10, –-9)
nmod(hurricanes-8, occur-10)
advmod(hurricanes-8, infrequently-11)
cc(cause-13, but-12)
conj(storms-4, cause-13)
obj(cause-13, devastation-14)
dep(devastation-14, that-15)
compound(resources-17, strains-16)
dep(that-15, resources-17)
case(point-20, to-18)
amod(point-20, breaking-19)
nmod(resources-17, point-20)
punct(storms-4, .-21)
~~~

8. Letters delivered on time by old-fashioned means are increasingly rare, so it is as well that that is not the only option available.  

- Gold standard: 

~~~ conllu
# this is one sentence
1	Letters	letter	NNS	NNS	_	12	nsubj	_	_
2	delivered	deliver	VBN	VBN	_	1	dep	_	_
3	on	on	IN	IN	_	4	case	_	_
4	time	time	NN	NN	_	2	obl	_	_
5	by	by	IN	IN	_	9	case	_	_
6	old	old	JJ	JJ	_	8	dep	_	_
7	-	-	HYPH	HYPH	_	6	punct	_	_
8	fashioned	fashioned	JJ	JJ	_	9	amod	_	_
9	means	means	NNS	NNS	_	2	obl	_	_
10	are	be	VBP	VBP	_	12	cop	_	_
11	increasingly	increasingly	RB	RB	_	12	advmod	_	_
12	rare	rare	JJ	JJ	_	0	root	_	_
13	,	,	,	,	_	14	punct	_	_
14	so	so	RB	RB	_	16	advmod	_	_
15	it	it	PRP	PRP	_	16	nsubj	_	_
16	is	be	VBZ	VBZ	_	12	dep	_	_
17	as	as	RB	RB	_	18	advmod	_	_
18	well	well	RB	RB	_	16	advmod	_	_
19	that	that	IN	IN	_	21	dep	_	_
20	that	that	DT	DT	_	21	nsubj	_	_
21	is	be	VBZ	VBZ	_	16	xcomp	_	_
22	not	not	RB	RB	_	21	advmod	_	_
23	the	the	DT	DT	_	25	det	_	_
24	only	only	JJ	JJ	_	25	amod	_	_
25	option	option	NN	NN	_	22	obl:npmod	_	_
26	available	available	JJ	JJ	_	25	amod	_	_
27	.	.	.	.	_	12	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
Letters/NNPS delivered/VBN on/IN time/NN by/IN old/JJ -/HYPH fashioned/JJ means/NNS are/VBP increasingly/RB rare/JJ ,/, so/IN it/PRP is/VBZ as/RB well/RB that/IN that/DT is/VBZ not/RB the/DT only/JJ option/NN available/JJ ./.
nsubj(rare-12, Letters-1)
acl(Letters-1, delivered-2)
case(time-4, on-3)
obl:on(delivered-2, time-4)
case(means-9, by-5)
amod(fashioned-8, old-6)
punct(fashioned-8, --7)
amod(means-9, fashioned-8)
obl:by(delivered-2, means-9)
cop(rare-12, are-10)
advmod(rare-12, increasingly-11)
root(ROOT-0, rare-12)
mark(is-16, so-14)
nsubj(is-16, it-15)
advcl(rare-12, is-16)
advmod(is-16, as-17)
fixed(as-17, well-18)
mark(available-26, that-19)
nsubj(available-26, that-20)
cop(available-26, is-21)
advmod(available-26, not-22)
det(option-25, the-23)
amod(option-25, only-24)
obl:npmod(available-26, option-25)
advcl(as-17, available-26)
~~~

- NN-based dependency parser:

~~~ sdparse
Letters/NNPS, delivered/VBD, on/IN, time/NN, by/IN, old/JJ, -/HYPH, fashioned/JJ, means/NNS, are/VBP, increasingly/RB, rare/JJ, ,/,, so/IN, it/PRP, is/VBZ, as/RB, well/RB, that/IN, that/DT, is/VBZ, not/RB, the/DT, only/JJ, option/NN, available/JJ, ./.
nsubj(delivered-2, Letters-1)
subj(rare-12, delivered-2)
case(time-4, on-3)
obl(delivered-2, time-4)
case(means-9, by-5)
amod(fashioned-8, old-6)
punct(fashioned-8, --7)
amod(means-9, fashioned-8)
obl(delivered-2, means-9)
cop(rare-12, are-10)
advmod(rare-12, increasingly-11)
root(ROOT-0, rare-12)
punct(rare-12, ,-13)
mark(option-25, so-14)
nsubj(option-25, it-15)
cop(option-25, is-16)
cc(option-25, as-17)
fixed(as-17, well-18)
fixed(as-17, that-19)
nsubj(option-25, that-20)
cop(option-25, is-21)
advmod(option-25, not-22)
det(option-25, the-23)
amod(option-25, only-24)
advcl(rare-12, option-25)
amod(option-25, available-26)
punct(rare-12, .-27)
~~~

9. English also has many words of more or less unique function, including interjections (oh, ah), negatives (no, not), politeness markers (please, thank you), and the existential 'there' (there are horses but not unicorns) among others.  

- Gold standard: 

~~~ conllu
# this is one sentence
1	English	English	NNP	NNP	_	3	nsubj	_	_
2	also	also	RB	RB	_	3	advmod	_	_
3	has	have	VBZ	VBZ	_	0	root	_	_
4	many	many	JJ	JJ	_	5	amod	_	_
5	words	word	NNS	NNS	_	3	obj	_	_
6	of	of	IN	IN	_	11	case	_	_
7	more	more	JJR	JJR	_	11	amod	_	_
8	or	or	CC	CC	_	7	cc	_	_
9	less	less	JJR	JJR	_	8	dep	_	_
10	unique	unique	JJ	JJ	_	11	amod	_	_
11	function	function	NN	NN	_	5	nmod	_	_
12	,	,	,	,	_	13	punct	_	_
13	includeing	includee	VBG	VBG	_	11	dep	_	_
14	interjections	interjection	NNS	NNS	_	13	obj	_	_
15	(	(	-LRB-	-LRB-	_	18	punct	_	_
16	oh	oh	UH	UH	_	18	dep	_	_
17	,	,	,	,	_	16	punct	_	_
18	ah	ah	UH	UH	_	14	dep	_	_
19	)	)	-RRB-	-RRB-	_	18	punct	_	_
20	,	,	,	,	_	13	punct	_	_
21	negatives	negative	NNS	NNS	_	13	conj	_	_
22	(	(	-LRB-	-LRB-	_	25	punct	_	_
23	no	no	RB	RB	_	25	dep	_	_
24	,	,	,	,	_	23	punct	_	_
25	not	not	RB	RB	_	21	dep	_	_
26	)	)	-RRB-	-RRB-	_	25	punct	_	_
27	,	,	,	,	_	13	punct	_	_
28	politeness	politeness	NN	NN	_	29	compound	_	_
29	markers	marker	NNS	NNS	_	13	conj	_	_
30	(	(	-LRB-	-LRB-	_	33	punct	_	_
31	please	please	UH	UH	_	33	dep	_	_
32	,	,	,	,	_	31	punct	_	_
33	thank	thank	VB	VB	_	29	dep	_	_
34	you	you	PRP	PRP	_	33	obj	_	_
35	)	)	-RRB-	-RRB-	_	33	punct	_	_
36	,	,	,	,	_	13	punct	_	_
37	and	and	CC	CC	_	13	cc	_	_
38	the	the	DT	DT	_	41	dep	_	_
39	existential	existential	JJ	JJ	_	41	dep	_	_
40	'	'	``	``	_	41	punct	_	_
41	there	there	RB	RB	_	37	dep	_	_
42	'	'	''	''	_	41	punct	_	_
43	(	(	-LRB-	-LRB-	_	45	punct	_	_
44	there	there	EX	EX	_	45	dep	_	_
45	are	be	VBP	VBP	_	41	dep	_	_
46	horses	horse	NNS	NNS	_	45	dep	_	_
47	but	but	CC	CC	_	46	cc	_	_
48	not	not	RB	RB	_	47	dep	_	_
49	unicorns	unicorn	NNS	NNS	_	47	dep	_	_
50	)	)	-RRB-	-RRB-	_	13	punct	_	_
51	among	among	IN	IN	_	52	case	_	_
52	others	other	NNS	NNS	_	13	obl	_	_
53	.	.	.	.	_	3	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
English/NNP also/RB has/VBZ many/JJ words/NNS of/IN more/RBR or/CC less/RBR unique/JJ function/NN ,/, including/VBG interjections/NNS (/-LRB- oh/CD ,/, ah/JJ )/-RRB- ,/, negatives/NNS (/-LRB- no/UH ,/, not/RB )/-RRB- ,/, politeness/JJ markers/NNS (/-LRB- please/UH ,/, thank/UH you/PRP )/-RRB- ,/, and/CC the/DT existential/JJ '/`` there/RB '/'' (/-LRB- there/EX are/VBP horses/NNS but/CC not/RB unicorns/NNS )/-RRB- among/IN others/NNS ./.
nsubj(has-3, English-1)
advmod(has-3, also-2)
root(ROOT-0, has-3)
amod(words-5, many-4)
obj(has-3, words-5)
case(function-11, of-6)
advmod(unique-10, more-7)
cc(less-9, or-8)
conj:or(more-7, less-9)
advmod(unique-10, less-9)
amod(function-11, unique-10)
nmod:of(words-5, function-11)
case(interjections-14, including-13)
nmod:including(function-11, interjections-14)
dep(interjections-14, oh-16)
dep(oh-16, ah-18)
nmod:including(function-11, negatives-21)
conj:and(interjections-14, negatives-21)
discourse(not-25, no-23)
dep(negatives-21, not-25)
amod(markers-29, politeness-28)
nmod:including(function-11, markers-29)
conj:and(interjections-14, markers-29)
discourse(you-34, please-31)
dep(please-31, thank-33)
dep(markers-29, you-34)
cc(there-41, and-37)
det(there-41, the-38)
amod(there-41, existential-39)
nmod:including(function-11, there-41)
conj:and(interjections-14, there-41)
expl(are-45, there-44)
dep(words-5, are-45)
nsubj(are-45, horses-46)
cc(not-48, but-47)
cc(unicorns-49, not-48)
nsubj(are-45, unicorns-49)
conj:negcc(horses-46, unicorns-49)
case(others-52, among-51)
nmod:among(words-5, others-52)
~~~

- NN-based dependency parser:

~~~ sdparse
English/NNP, also/RB, has/VBZ, many/JJ, words/NNS, of/IN, more/RBR, or/CC, less/RBR, unique/JJ, function/NN, ,/,, including/VBG, interjections/NNS, (/-LRB-, oh/UH, ,/,, ah/UH, )/-RRB-, ,/,, negatives/NNS, (/-LRB-, no/UH, ,/,, not/RB, )/-RRB-, ,/,, politeness/NN, markers/NNS, (/-LRB-, please/UH, ,/,, thank/VBP, you/PRP, )/-RRB-, ,/,, and/CC, the/DT, existential/JJ, '/``, there/EX, '/'', (/-LRB-, there/EX, are/VBP, horses/NNS, but/CC, not/RB, unicorns/NNS, )/-RRB-, among/IN, others/NNS, ./.
nsubj(has-3, English-1)
advmod(has-3, also-2)
root(ROOT-0, has-3)
amod(words-5, many-4)
obj(has-3, words-5)
case(function-11, of-6)
advmod(unique-10, more-7)
cc(less-9, or-8)
conj(more-7, less-9)
amod(function-11, unique-10)
nmod(words-5, function-11)
punct(words-5, ,-12)
case(interjections-14, including-13)
nmod(words-5, interjections-14)
punct(interjections-14, (-15)
discourse(interjections-14, oh-16)
punct(oh-16, ,-17)
dep(oh-16, ah-18)
punct(interjections-14, )-19)
punct(interjections-14, ,-20)
conj(interjections-14, negatives-21)
punct(not-25, (-22)
discourse(not-25, no-23)
punct(not-25, ,-24)
dep(negatives-21, not-25)
punct(not-25, )-26)
punct(interjections-14, ,-27)
compound(markers-29, politeness-28)
conj(interjections-14, markers-29)
punct(thank-33, (-30)
discourse(thank-33, please-31)
punct(thank-33, ,-32)
dep(markers-29, thank-33)
obj(thank-33, you-34)
punct(thank-33, )-35)
punct(interjections-14, ,-36)
cc(existential-39, and-37)
det(existential-39, the-38)
conj(interjections-14, existential-39)
punct(existential-39, '-40)
dep(existential-39, there-41)
punct(existential-39, '-42)
punct(are-45, (-43)
expl(are-45, there-44)
parataxis(has-3, are-45)
nsubj(are-45, horses-46)
cc(not-48, but-47)
cc(unicorns-49, not-48)
conj(horses-46, unicorns-49)
punct(are-45, )-50)
case(others-52, among-51)
obl(has-3, others-52)
punct(has-3, .-53)
~~~

10(a). The Penn Treebank tagset was culled from the original 87-tag tagset for the Brown Corpus.

- Gold standard: 

~~~ conllu
# this is one sentence
1	The	the	DT	DT	_	2	det	_	_
2	Penn	Penn	NNP	NNP	_	5	nsubj	_	_
3	Treebank	Treebank	NNP	NNP	_	2	dep	_	_
4	tagset	tagset	NN	NN	_	3	dep	_	_
5	was	be	VBD	VBD	_	0	root	_	_
6	culled	cull	VBN	VBN	_	5	dep	_	_
7	from	from	IN	IN	_	13	case	_	_
8	the	the	DT	DT	_	13	det	_	_
9	original	original	JJ	JJ	_	13	amod	_	_
10	87	87	CD	CD	_	9	dep	_	_
11	-	-	HYPH	HYPH	_	10	punct	_	_
12	tag	tag	NN	NN	_	10	dep	_	_
13	tagset	tagset	NN	NN	_	5	obl	_	_
14	for	for	IN	IN	_	16	case	_	_
15	the	the	DT	DT	_	16	det	_	_
16	Brown	Brown	NNP	NNP	_	13	nmod	_	_
17	corpus	corpus	NNP	NNP	_	16	dep	_	_
18	.	.	.	.	_	5	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
The/DT Penn/NNP Treebank/NNP tagset/NNP was/VBD culled/VBN from/IN the/DT original/JJ 87/CD -/HYPH tag/NN tagset/NN for/IN the/DT Brown/NNP Corpus/NNP ./.
det(tagset-4, The-1)
compound(tagset-4, Penn-2)
compound(tagset-4, Treebank-3)
nsubj:pass(culled-6, tagset-4)
aux:pass(culled-6, was-5)
root(ROOT-0, culled-6)
case(tagset-13, from-7)
det(tagset-13, the-8)
amod(tagset-13, original-9)
nummod(tag-12, 87-10)
punct(tag-12, --11)
compound(tagset-13, tag-12)
obl:from(culled-6, tagset-13)
case(Corpus-17, for-14)
det(Corpus-17, the-15)
compound(Corpus-17, Brown-16)
nmod:for(tagset-13, Corpus-17)
~~~

- NN-based dependency parser:

~~~ sdparse
The/DT, Penn/NNP, Treebank/NNP, tagset/NN, was/VBD, culled/VBN, from/IN, the/DT, original/JJ, 87/CD, -/HYPH, tag/NN, tagset/NN, for/IN, the/DT, Brown/NNP, Corpus/NNP, ./.
det(tagset-4, The-1)
compound(Treebank-3, Penn-2)
compound(tagset-4, Treebank-3)
nsubj:pass(culled-6, tagset-4)
aux:pass(culled-6, was-5)
root(ROOT-0, culled-6)
case(tagset-13, from-7)
det(tagset-13, the-8)
amod(tagset-13, original-9)
nummod(tag-12, 87-10)
punct(tag-12, --11)
compound(tagset-13, tag-12)
obl(culled-6, tagset-13)
case(Corpus-17, for-14)
det(Corpus-17, the-15)
compound(Corpus-17, Brown-16)
nmod(tagset-13, Corpus-17)
punct(culled-6, .-18)
~~~

10(b). For example the original Brown and C5 tagsets include a separate tag for each of the different forms of the verbs do (e.g. C5 tag VDD for did and VDG tag for doing), be and have.

- Gold standard: 

~~~ conllu
# this is one sentence
1	For	for	IN	IN	_	2	case	_	_
2	example	example	NN	NN	_	9	obl	_	_
3	the	the	T	DT	_	4	det	_	_
4	original	original	JJ	JJ	_	9	nsubj	_	_
5	Brown	Brown	NNP	NNP	_	4	dep	_	_
6	and	and	CC	CC	_	4	cc	_	_
7	C5	C5	NNP	NNP	_	8	compound	_	_
8	tagsets	tagset	NNS	NNS	_	6	dep	_	_
9	include	include	VBP	VBP	_	0	root	_	_
10	a	a	DT	DT	_	11	det	_	_
11	separate	separate	JJ	JJ	_	9	obj	_	_
12	tag	tag	NN	NN	_	11	dep	_	_
13	for	for	IN	IN	_	14	case	_	_
14	each	each	DT	DT	_	12	nmod	_	_
15	of	of	IN	IN	_	17	case	_	_
16	the	the	DT	DT	_	17	det	_	_
17	different	different	JJ	JJ	_	14	obl	_	_
18	forms	form	NNS	NNS	_	17	dep	_	_
19	of	of	IN	IN	_	21	case	_	_
20	the	the	DT	DT	_	21	det	_	_
21	verbs	verb	NNS	NNS	_	18	nmod	_	_
22	do	do	VB	VB	_	24	dep	_	_
23	(	(	-LRB-	-LRB-	_	24	punct	_	_
24	e.g.	e.g.	RB	RB	_	37	dep	_	_
25	C5	C5	NNP	NNP	_	24	obl:npmod	_	_
26	tag	tag	NN	NN	_	27	compound	_	_
27	VDD	vdd	NN	NN	_	25	dep	_	_
28	for	for	IN	IN	_	29	case	_	_
29	did	do	VBN	VBN	_	24	advcl	_	_
30	and	and	CC	CC	_	24	cc	_	_
31	VDG	vdg	NN	NN	_	32	compound	_	_
32	tag	tag	NN	NN	_	30	dep	_	_
33	for	for	IN	IN	_	34	case	_	_
34	doing	do	VBG	VBG	_	30	dep	_	_
35	)	)	-RRB-	-RRB-	_	24	punct	_	_
36	,	,	,	,	_	37	punct	_	_
37	be	be	VB	VB	_	38	dep	_	_
38	and	and	CC	CC	_	21	dep	_	_
39	have	VERB	VERB	VB	_	38	dep	_	_
40	.	.	.	.	_	9	punct	_	_

~~~

- Unlexicalised PCFG:

~~~ sdparse
For/IN example/NN the/DT original/JJ Brown/NNP and/CC C5/NNP tagsets/NNS include/VBP a/DT separate/JJ tag/NN for/IN each/DT of/IN the/DT different/JJ forms/NNS of/IN the/DT verbs/NNS do/VB (/-LRB- e.g./FW C5/NNP tag/NNP VDD/NNP for/IN did/VBD and/CC VDG/VBD tag/NN for/IN doing/VBG )/-RRB- ,/, be/VB and/CC have/VB ./.
case(example-2, For-1)
obl:for(include-9, example-2)
det(tagsets-8, the-3)
amod(tagsets-8, original-4)
compound(tagsets-8, Brown-5)
cc(C5-7, and-6)
conj:and(Brown-5, C5-7)
compound(tagsets-8, C5-7)
nsubj(include-9, tagsets-8)
root(ROOT-0, include-9)
det(tag-12, a-10)
amod(tag-12, separate-11)
nsubj(do-22, tag-12)
nsubj(be-37, tag-12)
nsubj(have-39, tag-12)
case(each-14, for-13)
nmod:for(tag-12, each-14)
case(forms-18, of-15)
det(forms-18, the-16)
amod(forms-18, different-17)
nmod:of(each-14, forms-18)
case(verbs-21, of-19)
det(verbs-21, the-20)
nmod:of(forms-18, verbs-21)
ccomp(include-9, do-22)
dep(VDD-27, e.g.-24)
compound(VDD-27, C5-25)
compound(VDD-27, tag-26)
dep(do-22, VDD-27)
mark(did-29, for-28)
dep(VDD-27, did-29)
cc(VDG-31, and-30)
dep(VDD-27, VDG-31)
conj:and(did-29, VDG-31)
obj(did-29, tag-32)
mark(doing-34, for-33)
advcl(did-29, doing-34)
ccomp(include-9, be-37)
conj:and(do-22, be-37)
cc(have-39, and-38)
ccomp(include-9, have-39)
conj:and(do-22, have-39)
~~~

- NN-based dependency parser:

~~~ sdparse
For/IN, example/NN, the/DT, original/JJ, Brown/NNP, and/CC, C5/NN, tagsets/NNS, include/VBP, a/DT, separate/JJ, tag/NN, for/IN, each/DT, of/IN, the/DT, different/JJ, forms/NNS, of/IN, the/DT, verbs/NNS, do/VBP, (/-LRB-, e.g./FW, C5/NN, tag/NN, VDD/NN, for/IN, did/VBD, and/CC, VDG/NNP, tag/NN, for/IN, doing/VBG, )/-RRB-, ,/,, be/VB, and/CC, have/VB, ./.
case(example-2, For-1)
obl(include-9, example-2)
det(tagsets-8, the-3)
amod(tagsets-8, original-4)
compound(tagsets-8, Brown-5)
cc(C5-7, and-6)
conj(Brown-5, C5-7)
nsubj(include-9, tagsets-8)
root(ROOT-0, include-9)
det(tag-12, a-10)
amod(tag-12, separate-11)
obj(include-9, tag-12)
case(each-14, for-13)
nmod(tag-12, each-14)
case(forms-18, of-15)
det(forms-18, the-16)
amod(forms-18, different-17)
nmod(each-14, forms-18)
case(verbs-21, of-19)
det(verbs-21, the-20)
nmod(forms-18, verbs-21)
dep(tag-12, do-22)
punct(VDD-27, (-23)
advmod(VDD-27, e.g.-24)
compound(VDD-27, C5-25)
compound(VDD-27, tag-26)
dep(do-22, VDD-27)
mark(tag-32, for-28)
aux(tag-32, did-29)
cc(tag-32, and-30)
compound(tag-32, VDG-31)
acl(VDD-27, tag-32)
mark(doing-34, for-33)
advcl(tag-32, doing-34)
punct(VDD-27, )-35)
punct(VDD-27, ,-36)
dep(VDD-27, be-37)
cc(have-39, and-38)
conj(be-37, have-39)
punct(include-9, .-40)
~~~


This is a page of documentation created using the Annodoc
system. It serves a double purpose as *documentation* for the Annodoc
system and as a *template* that you can use as a starting point for
creating your own documentation using annodoc.

## Table of contents

* [What is Annodoc?](#what-is-annodoc)
* [How does it work?](#how-does-it-work)
* [Getting started](#getting-started)
* [Editing documents](#editing-documents)
* [Adding documents](#adding-documents)
* [Visualizations](#visualizations)
* [Collections](#collections)
* [Configuration](#configuration)
* [Troubleshooting](#troubleshooting)

## What is Annodoc?

Annodoc is a documentation support system focusing in particular on
guidelines for text annotation. The system combines ease of editing
using a simple plain-text like format with support for the
visualization of complex, structured text annotation and close
integration with version control.

A brief
[introduction of Annodoc](http://www2.lingfil.uu.se/SLTC2014/abstracts/sltc2014_submission_32.pdf)
[PDF] was presented at
[SLTC'14](http://www2.lingfil.uu.se/SLTC2014/).

For example, consider the following fragment of documentation

<div class="documentation-example" markdown="1">
Mentions of person names are annotated as [PERSON]()

~~~ ann
Barack Obama is the current president.
T1 PERSON 0 12 Barack Obama
~~~

<span style="float:right;font-size:75%;opacity:0.5">(Not seeing a visualization above? See <a href="#troubleshooting">troubleshooting</a>)</span>

</div>

this example is generated from the following input:

    Mentions of person names are annotated as [PERSON]()

    ~~~ ann
    Barack Obama is the current president.
    T1 PERSON 0 12 Barack Obama
    ~~~

## How does it work?

The text content of Annodoc documents is in the simple [Markdown]
format (with the option to include HTML), and the data for the
visualizations is represented in any of a number of supported
annotation formats such as [Stanford dependency], [CoNLL-X], 
[CoNLL-U], or [.ann standoff].

The final documents seen in the browser are a combination of (X)HTML
and [SVG] for the visualizations. The primary tools for generating the
final documents from the source are the [Jekyll] static web site
generator, which converts Markdown into (X)HTML, and the [brat]
annotation tool, which generates the SVG visualizations, with help
from some Annodoc-specific extensions.

The following figure shows the primary stages of processing.

<img style="width:100%" src="static/img/processing.png">

In addition to Markdown processing, Jekyll provides numerous other
features such as document collection management as well as templating
and simple scripting using the [Liquid] language, and Annodoc provides
various facilities for supporting guideline development such as
automatic linking of defined types.

Finally, to support the development and maintenance of complex sets of
documentation, Annodoc features close integration with the [Git]
distributed version control system through the [GitHub] web-based
hosting service, allowing automatic conversion and publication of the
most recent version of the online documentation each time the sources
are updated.

For more information on these technologies, please see the following:

* Jekyll: <http://jekyllrb.com/>
* brat: <http://brat.nlplab.org>
* Markdown: <http://daringfireball.net/projects/markdown/>
* Kramdown (Markdown superset): <http://kramdown.gettalong.org/>
* Liquid: <http://wiki.shopify.com/Liquid>
* Stanford Dependency format: <http://nlp.stanford.edu/software/stanford-dependencies.shtml>
* CoNLL-X format: <http://ilk.uvt.nl/conll/#dataformat>
* CoNLL-U format: <http://universaldependencies.github.io/docs/format.html>
* .ann standoff format: <http://brat.nlplab.org/standoff.html>
* Git: <http://git-scm.com/>
* GitHub: <http://github.com>

## Getting started

First, you need to get a copy of the Annodoc system. If you don't have
one already, head over to the online [Annodoc repository] and
download, clone or fork the repository. The former two options
(download or clone) will give you a local copy of the system (see
[running locally](#running-locally) below), while cloning the
repository can allow you to work within the online version control
system (see [working online](#working-online)).

To **download** the system source, navigate to the [Annodoc
repository] and click on the `Download ZIP` link on the right-hand
toolbar. You should then unpack the downloaded `.zip` file in an
appropriate location and move to the directory with the source.  For
the next steps, see [running locally](#running-locally) below.

To **clone** the system, you will need the [Git] version control
system. After making sure that Git is available, navigate to the
[Annodoc repository] and copy the "clone URL" from the right-hand
toolbar. Then, run the command `git clone <URL>`, where `<URL>` is the
clone URL copied previously. Finally, move to the cloned directory and
see [running locally](#running-locally) below for the next steps.

To **fork** the system, you will need a GitHub account. Then, while
logged in to GitHub, navigate to the [Annodoc repository] and click on
the `Fork` button on the top right. This will give you a copy of the
repository that you can work on in GitHub. You can then download or
clone this copy, as above, to [run the system
locally](#running-locally), or [work online](#working-online) (see
below).

### Running locally

**Please note**: the Annodoc system has been developed and tested in a
linux environment and has so far not been specifically tested on
Windows.  We strongly recommend a Unix or workalike system (OSX or
linux) for running the system locally.

For running Annodoc locally, you will need to have a recent version of
[Jekyll]. In particular, version 2.0 or greater is required for
[collection](#collections) features.

After getting a local copy of the system (see [Getting
started](#getting-started) above), you can build the site from sources
and serve the resulting documents by navigating to the directory with
annodoc sources and using the command

```
jekyll serve --watch
```

(here, the option `--watch` specifies that Jekyll should watch the
source documents for changes and rebuild the site when there are any.)

If the above command runs successfully, you should see something like
the following:

<pre><code>$ jekyll serve --watch
            Source: .
       Destination: ./_site
      Generating... done.
 Auto-regeneration: enabled
    Server address: http://0.0.0.0:4000/
  Server running... press ctrl-c to stop.</code></pre>

Here, the value `Server address` (commonly `http://0.0.0.0:4000/`) is
a URL where Jekyll is serving the site from. You should be able to see
the documentation by navigating to this address using your browser.
If you do not see the documentation at this address, please see
[troubleshooting](#troubleshooting) below.

### Working online

In addition to running Jekyll locally (see [running
locally](#running-locally)), it is possible to use the Annodoc system
entirely online, relying on the facilities of [GitHub] (or a
workalike) for generating the site from source using Jekyll. The
following assumes that the repository is stored in [GitHub] unless
separately mentioned.

GitHub provides website hosting with Jekyll support through [GitHub
pages](https://pages.github.com/). Using GitHub pages with a GitHub
repository is largely automatic: simply make sure that the source
documents are held in the `gh-pages` branch of your repository, and
the processed final documents will be automatically made available at
`http://username.github.io/repository`, where `username` is your
GitHub username and `repository` is the name of the repository.

**Note:** GitHub pages are publicly visible even for private GitHub
repositories.

For further information setting up GitHub pages, please refer to the
documentation at <https://pages.github.com/>.

## Editing documents

You can either edit source documents directly in your favorite text
editor, or via a simple online interface.

### Editing locally

If you have a local copy of an Annodoc system (see [Getting
started](#getting-started) above), you can edit any of the source
documents directly, using any text editor.

Most typically, changes are made to one or more Markdown (`.md`)
files. To see the effect of these changes in the final documentation,
the source needs to be processed through Jekyll. (see [Running
locally](#running-locally); note that this processing is automatic
with the `--watch` option).

If you are working with Git for version control, you should commit and
push your changes to the Git repository when you are done, e.g. by
running the following

    git commit DOCUMENT.md
    git push

(where `DOCUMENT.md` is the name of the changed document.)

Alternatively, you can run `git commit -a` to commit all changed
documents.

### Editing online

If you are working with a repository stored in GitHub (or similar),
you can use online editing features.

**Please note**: the "edit page" link will only appear if the
`editurl` site variable is set in `_config.yml` (see
[Configuration](#configuration)). Please make sure that your
configuration is correctly set up to use these features.

When configured for online editing, the header of each Annodoc
documentation page will contain an "edit page" link that leads to the
[GitHub] online editing page, shown in the following:

<img style="width:100%; border:1px solid lightgray" src="static/img/gh-edit.png">

This feature allows version-controlled documents to be edited directly
from your browser. To get started, the only relevant parts are the
large black edit area and the "Cancel" and "Commit changes" buttons at
the bottom.

To give this a quick try, click on the following link: [edit sandbox
document]({{ site.editurl }}/sandbox.md).  This should open a
"sandbox" document in a new tab. (If this does not work, please see
[troubleshooting](#troubleshooting) below.) After testing it out, feel
free to either cancel without saving your changes, or save them into
the version control system using the "Commit changes" button. You can
see the resulting document here (reload to see changes, and please
note it may take some time for the changes to show up.)

For experimenting with the system, we recommend using the sandbox
document instead of any "real" documents.

To edit the actual documentation, first find the page you're
interested in. Then,

* Click on the "edit page" link on the top
* Make your changes in the GitHub editor
* (Optional: add a message describing your changes in the "Commit changes" box)
* Click on "Commit changes"

Finally, wait a moment for your revisions to the documentation to be
compiled (normally no more than 10 seconds) and reload the
documentation page to make sure they look right.

## Adding documents

To add new documents into the system, simply create a new `.md`
document and add the following front matter at the beginning of the
document:

    ---
    layout: entry
    title: DOCUMENT-TITLE
    ---

(where `DOCUMENT-TITLE` is the title you wish to give to the
document.)

This [YAML] front matter is required for Jekyll to identify the
document as markdown.

If you are using the GitHub (or similar), you can create new documents
simply by clicking on the `+` sign at the top or the repository file
listing.

If you are working locally with Git for version control, you can
create new documents with any text editor and then add newly created
documents to the Git repository, e.g. by running the following
commands:

    git add DOCUMENT.md
    git commit
    git push

(where `DOCUMENT.md` is the name of the new document.)

## Visualizations

As explained in the section [what is annodoc?](#what-is-annodoc),
visualizations are created using a simple syntax that identifies a
section of the document as being annotation in some particular format.
The system then replaces these sections with the corresponding
visualizations.

This section provides examples of various ways to create
visualizations.

### Visualization basics

There are a number of ways to add visualizations into a document.  The
most straightforward one is to wrap annotations in a format `FORMAT`
with the lines `~~~ FORMAT` (before) and `~~~` (after). For example,

    ~~~ ann
    Barack Obama is the current president.
    T1 PERSON 0 12 Barack Obama
    ~~~

gives the following visualization:

~~~ ann
Barack Obama is the current president.
T1 PERSON 0 12 Barack Obama
~~~

Above, the `FORMAT` value `ann` specifies that the source content is
in the [.ann standoff] format. Currently, the following formats are
supported:

* .ann standoff format: <http://brat.nlplab.org/standoff.html>
* Stanford Dependency format: <http://nlp.stanford.edu/software/stanford-dependencies.shtml>
* CoNLL-X format: <http://ilk.uvt.nl/conll/#dataformat>
* CoNLL-U format: <http://universaldependencies.github.io/docs/format.html>

Some more simple examples follow.

A single tree in the Stanford Dependency format can be embedded using
the following syntax:

    ~~~ sdparse
    Dogs run
    nsubj(run, Dogs)
    ~~~

which results in this embedded visualization:

~~~ sdparse
Dogs run
nsubj(run, Dogs)
~~~

Parses represented in the CoNLL-X format can be embedded as illustrated
by the following example:

    ~~~ conllx
    1    Dogs   dog    _    NNS    _    2    nsubj
    2    run    run    _    VBP    _    0    ROOT
    ~~~

gives

~~~ conllx
1    Dogs   dog    _    NNS    _    2    nsubj
2    run    run    _    VBP    _    0    ROOT
~~~

Finally, parses in the CoNLL-U format can be embedded as shown below:

    ~~~ conllu
    1    They    they    PRON    PRN    Case=Nom|Num=Plur            2    nsubj    _    _
    2    buy     buy     VERB    VBP    Num=Plur|Per=3|Tense=Pres    0    root     _    _
    3    books   book    NOUN    NNS    Num=Plur                     2    dobj     _    _
    ~~~

resulting in

~~~ conllu
1    They    they    PRON    PRN    Case=Nom|Num=Plur            2    nsubj    _    _
2    buy     buy     VERB    VBP    Num=Plur|Per=3|Tense=Pres    0    root     _    _
3    books   book    NOUN    NNS    Num=Plur                     2    dobj     _    _
~~~

The remainder of this section provides further details for each
supported format and additional information on options for embedding
visualizations.

### .ann standoff format

This section provides information on the .ann standoff (Ann) format.
For full documentation, please refer to
<http://brat.nlplab.org/standoff.html>.

#### Ann format: annotation primitives

The following example illustrates some of the basic Ann format
annotation primitives that are supported in visualizations. The
annotation

    ~~~ ann
    Sony formed a joint venture with Ericsson, a company based in Sweden.
    T1 Organization 0 4	Sony
    T2 MERGE-ORG 14 27	joint venture
    T3 Organization 33 41	Ericsson
    E1 MERGE-ORG:T2 Org1:T1 Org2:T3
    T4 Country 62 68	Sweden
    R1 Origin Arg1:T3 Arg2:T4
    A1 Name T4
    ~~~

is visualized as follows:

~~~ ann
Sony formed a joint venture with Ericsson, a company based in Sweden.
T1 Organization 0 4	Sony
T2 MERGE-ORG 14 27	joint venture
T3 Organization 33 41	Ericsson
E1 MERGE-ORG:T2 Org1:T1 Org2:T3
T4 Country 62 68	Sweden
R1 Origin Arg1:T3 Arg2:T4
A1 Name T4
~~~

This example involves *text-bound* annotations, an *attribute*
annotation, an *event* annotation, and a *relation* annotation. All
annotations occupy a single line of the input and begin with a unique
identifier. The remaining structure varies depending on the annotation
primitive.

#### Ann format: text-bound annotations

Text-bound annotations identify a span of text using `(start, end)`
offsets and assign it a type (note that the marked text is repeated
for reference):

    T1 Organization 0 4	Sony
    T2 MERGE-ORG 14 27	joint venture
    T3 Organization 33 41	Ericsson
    T4 Country 75 81	Sweden

Text-bound annotations can be used, for example, to mark mentions of
specific named entities in text (`Sony`, `Ericsson` and `Sweden`
above) or the "triggers" of event annotations (`joint venture`).

In addition to simple `(start, end)` spans, discontinuous span
annotations are also supported using the syntax `START END[;START
END[...]]`. For example,

    ~~~ ann
    Barack and Michelle Obama
    T1 PERSON 0 6;20 25 Barack Obama
    T2 PERSON 11 19 Michelle
    ~~~

gives

~~~ ann
Barack and Michelle Obama
T1 PERSON 0 6;20 25 Barack Obama
T2 PERSON 11 19 Michelle
~~~

#### Ann format: attribute annotations

Attribute annotation associate either a binary flag (e.g. `IsName`) or
a key-value pair (e.g. `Tense`, `Past`) with another annotation, such
as an entity mention (textbound) or an event annotation.

    A1 IsName T4
    A2 Tense E1 Past

#### Ann format: relation annotations

Relation annotations relate two other annotations and have a type
(e.g. `Origin`).

    R1 Origin Arg1:T3 Arg2:T4

#### Ann format: event annotations

Event annotations associate any number of annotations in specific
roles (e.g. `Theme`, `Cause`), identifying the event with a type
(e.g. `MERGE-ORG`) and a textbound annotation expressing it in text.

    E1 MERGE-ORG:T2 Org1:T1 Org2:T3

#### Ann format: other annotation primitives

The [.ann standoff] format additionally supports equivalence
relations, normalization annotations and comment (or note)
annotations. These annotation primitives are presently not supported
in Annodoc.

### Stanford Dependency format

This section provides details on the Stanford Dependency (SD) format.

#### SD format basics

Basic SD format visualizations consist of a single line of text
followed by any number of typed dependencies between words using the
simple format `TYPE(FROM, TO)`. For example, the input

    ~~~ sdparse
    The quick brown fox jumped
    det(fox-4, The-1)
    amod(fox-4, quick-2)
    amod(fox-4, brown-3)
    nsubj(jumped-5, fox-4)
    ~~~

gives

~~~ sdparse
The quick brown fox jumped
det(fox-4, The-1)
amod(fox-4, quick-2)
amod(fox-4, brown-3)
nsubj(jumped-5, fox-4)
~~~

#### SD format: ambiguous tokens

If your example has several instances of the same token, you can use
their position to refer to the exact token. In the following example
`can-5` refers to the fifth token of the sentence, `can`.

    ~~~ sdparse
    I can can the can .
    nsubj(can-3, I)
    aux(can-3, can-2)
    det(can-5,the)
    dobj(can-3,can-5)
    punct(can-3,.)
    ~~~

will result in this visualization

~~~ sdparse
I can can the can .
nsubj(can-3, I)
aux(can-3, can-2)
det(can-5,the)
dobj(can-3,can-5)
punct(can-3,.)
~~~

#### SD format: part-of-speech tags

Part-of-speech (POS) tags are optional and use the format `text/POS`.

    ~~~ sdparse
    POS/NNP tags/NNS can/MD be/VB attached/VBN to/TO tokens/NNS ./.
    nn(tags, POS)
    nsubjpass(attached, tags)
    aux(attached, can)
    auxpass(attached, be)
    prep(attached, to)
    pobj(to, tokens)
    ~~~

~~~ sdparse
POS/NNP tags/NNS can/MD be/VB attached/VBN to/TO tokens/NNS ./.
nn(tags, POS)
nsubjpass(attached, tags)
aux(attached, can)
auxpass(attached, be)
prep(attached, to)
pobj(to, tokens)
~~~

If the source text contains any literal slashes (`/`), these can be
escaped using backslash.

     ~~~ sdparse
     \\/\\ escapes/VBZ :/: \\o\//\\o\/
     nsubj(escapes, \)
     ~~~

~~~ sdparse
\\/\\ escapes/VBZ :/: \\o\//\\o\/
nsubj(escapes, \)
~~~

### Multiple lines of text

The literal sequence `\n` in the SD input text is interpreted as a
newline. (This sequence should be separated by space from the rest of
the input.)

    ~~~ sdparse
    One line \n and another.
    ~~~

gives:

~~~ sdparse
One line \n and another.
~~~

### CoNLL-X format

This section provides information on the visualization of the CoNLL-X
format.

#### CoNLL-X format basics

The [CoNLL-X] format is a format for representing dependency parses,
developed as a variant of previous related formats for the 2006
CoNLL-X shared task on multi-lingual dependency parsing.

Each line in the CoNLL-X format specifies information relating to one
token (or word). For example, the following defines two words

    ~~~ conllx
    1    Dogs   dog    _    NNS    _    2    nsubj    _    _
    2    run    run    _    VBP    _    0    ROOT     _    _
    ~~~

visualized as

~~~ conllx
1    Dogs   dog    _    NNS    _    2    nsubj    _    _
2    run    run    _    VBP    _    0    ROOT     _    _
~~~

The definitions of the various space-separated fields are provided
in the following.

#### CoNLL-X format field definitions

The CoNLL-X format defines 10 fields separated by space (strictly TAB
characters in the original definition):

1. ID: Token counter, starting at 1 for each new sentence.
2. FORM: Word form or punctuation symbol.
3. LEMMA: Lemma or stem of word form.
4. CPOSTAG: Coarse-grained part-of-speech tag.
5. POSTAG: Fine-grained part-of-speech tag.
6. FEATS: Unordered set of syntactic and/or morphological features.
7. HEAD: Head of the current token.
8. DEPREL: Dependency relation to the HEAD.
9. PHEAD: Projective head of current token.
10. PDEPREL: Dependency relation to the PHEAD.

The current implementation of the visualization only uses the `ID`,
`FORM`, `CPOSTAG`, `HEAD` and `DEPREL` attributes.

### CoNLL-U format

This section provides information on the visualization of the [CoNLL-U]
format.

#### CoNLL-U format basics

The CoNLL-U format is a format for representing dependency parses,
developed in the 
[Universal Dependencies](universaldependencies.github.io/docs/)
project as a revision of the CoNLL-X format.

Most lines in CoNLL-U format specify the annotation of a single word
or token. The format uses blank lines to separate sentences (as in
CoNLL-X), and allows also comment lines beginning with the hash
character (`#`). The following example illustrates these:

    ~~~ conllu
    # this is one sentence
    1    Dogs   dog    NOUN    NNS    _    2    nsubj    _    _
    2    run    run    VERB    VBP    _    0    ROOT     _    _
    
    # this is a second sentence
    1    Cats   cat    NOUN    NNS    _    2    nsubj    _    _
    2    sleep  sleep  VERB    VBP    _    0    ROOT     _    _
    ~~~

~~~ conllu
# this is one sentence
1	My	my	PRON	PRP$	_	2	nmod:poss	_	_
2	aunt	aunt	NOUN	NN	_	7	nsubj	_	_
3	's	's	PART	POS	_	5	case	_	_
4	can	can	NOUN	NN	_	5	compound	_	_
5	opener	opener	NOUN	NN	_	2	nmod:poss	_	_
6	can	can	AUX	MD	_	7	aux	_	_
7	open	open	VERB	VB	_	0	root	_	_
8	a	a	DET	DT	_	9	det	_	_
9	drum	drum	NOUN	NN	_	7	obj	_	_
10	.	.	PUNCT	.	_	7	punct	_	_
~~~

#### CoNLL-U format field definitions

The CoNLL-U format defines 10 fields separated by space (strictly TAB
characters in the original definition):

 1. ID: Word index, integer starting at 1 for each new sentence; may be a range for tokens with multiple words.
 2. FORM: Word form or punctuation symbol.
 3. LEMMA: Lemma or stem of word form.
 4. CPOSTAG: Google universal part-of-speech tag from the [universal POS tag](http://universaldependencies.github.io/docs/u/pos/index.html) set.
 5. POSTAG: Language-specific part-of-speech tag; underscore if not available.
 6. FEATS: List of morphological features from the [universal feature inventory](http://universaldependencies.github.io/docs/u/feat/index.html) or from a defined language-specific extension; underscore if not available.
 7. HEAD: Head of the current token, which is either a value of ID or zero (0).
 8. DEPREL: [Universal Stanford dependency relation](http://universaldependencies.github.io/docs/u/dep/index.html) to the HEAD (root iff HEAD = 0) or a defined language-specific subtype of one.
 9. DEPS: List of secondary dependencies (head-deprel pairs).
10. MISC: Any other annotation.

For the complete documentation on the CoNLL-U format, please see
<http://universaldependencies.github.io/docs/format.html>.

### Alternative visualization syntaxes

As an alternative to the `~~~` syntax, you can use the equivalent HTML
tag form, where the format specification appears as the value of the
`class` attribute. For example,

    <div class="sdparse">
    Dogs run
    nsubj(run, Dogs)
    </div>

gives

<div class="sdparse">
Dogs run
nsubj(run, Dogs)
</div>

This form is more flexible in allowing e.g. additional attributes
to control aspects of the visualization. For example,

    <div class="sdparse" id="simple-example-parse" tabs="yes">
    Dogs run
    nsubj(run, Dogs)
    </div>

gives

<div class="sdparse" id="simple-example-parse" tabs="yes">
Dogs run
nsubj(run, Dogs)
</div>

(note the `edit` tab on the top right of the visualization.)

The Kramdown variant of Markdown provides an additional syntax for
specifying attributes called [Attribute List
Definitions](http://kramdown.gettalong.org/syntax.html#attribute-list-definitions)
(ALDs). Using ALDs, the above example can be alternatively written
as

    ~~~
    Dogs run
    nsubj(run, Dogs)
    ~~~
    {:.sdparse}

giving

~~~
Dogs run
nsubj(run, Dogs)
~~~
{:.sdparse}

ALDs can be used to specify arbitrary attributes. For example, the
`id` and `tabs` attributes can be specified as in the following:

    ~~~
    Dogs run
    nsubj(run, Dogs)
    ~~~
    {:#simple-example-parse-2 .sdparse tabs="yes"}

which gives

~~~
Dogs run
nsubj(run, Dogs)
~~~
{:#simple-example-parse-2 .sdparse tabs="yes"}

For full details on this feature, see
<http://kramdown.gettalong.org/syntax.html#attribute-list-definitions>.

### Other features

#### Editing controls

Controls for visualization editing and information is accessible in
elements with the attribute `tabs="yes"` (or any other non-empty
value):

    <div class="ann-annotation" tabs="yes">
    Barack Obama is the current president.
    T1 PERSON 0 12 Barack Obama
    </div>

This gives:

<div class="ann-annotation" tabs="yes">
Barack Obama is the current president.
T1 PERSON 0 12 Barack Obama
</div>

You can click on the tab on the top right to edit the visualization,
but note that the edits are not saved anywhere as there's no
server. This is mostly useful to build and debug examples.

#### Unicode

Everything is unicode-compliant.

    ~~~ sdparse
    ロボットは 東大に  入れる か 。/。
    nsubj(入れる, ロボットは)
    nommod(入れる, 東大に)
    ~~~

~~~ sdparse
ロボットは 東大に  入れる か 。/。
nsubj(入れる, ロボットは)
nommod(入れる, 東大に)
~~~

## Collections

[Jekyll collections](http://jekyllrb.com/docs/collections/) are a
recently introduced Jekyll feature that allows sets of related
documents to be grouped together. Collections support various
operations that specifically benefit guideline development, such as
automatic listings and generation of "merged" documents.

As an illustrative example, this Annodoc repository contains two
collections named `entity` and `relation` with a few example
documents. Using the [Liquid] language, this allows e.g. a listing
of documents in a specific collection to be created as follows:

{% raw %}
    {% for e in site.entity %}
    * {{ e.title }}
    {% endfor %}
{% endraw %}

which produces the following:

{% for e in site.entity %}
* {{ e.title }}
{% endfor %}

Alternatively, we can produce "merged" documents by importing the
contents of documents in collections. The following example shows
the contents of documents in the `entity` collection up to the
first `<!-- details -->` marker (if any):

{% raw %}
    {% for e in site.entity %}
    * {{ e.content | split:"<!-- details -->" | first }}
    {% endfor %}
{% endraw %}

which gives

{% for e in site.entity %}
* {{ e.content | split:"<!-- details -->" | first }}
{% endfor %}

We can similarly generate a listing of all collections, linking all
documents in those collections:

{% raw %}
    {% for c in site.collections %}
    * <b>Collection</b>: {{ c.label }}
      {% for d in c.docs %}
      * [{{ d.title }}]({{ d.url | remove_first:'/' }}): {{ d.shortdef }}
      {% endfor %}
    {% endfor %}
{% endraw %}

which gives

{% for c in site.collections %}
* <b>Collection</b>: {{ c.label }}
  {% for d in c.docs %}
  * [{{ d.title }}]({{ d.url | remove_first:'/' }}): {{ d.shortdef }}
  {% endfor %}
{% endfor %}

To add documents to a collection, simply add them to the corresponding
directory (e.g. `_type/` for the collection `type`). To add new
collections to the system, first create the directory, and then add
the corresponding entry to `collections` in `_config.yml` (see
[Configuration](#configuration) below).

It is recommended to organize (non-overlapping) sets of related
documents into collections. To get the most out of your Jekyll
collections, please refer also to the Liquid language documentation at
<http://wiki.shopify.com/Liquid>.

### Linking to collection entries

It is often necessary to cross-reference parts of documentation from
others. To make creating such links easier, Annodoc provides support
for linking to collection entries.

The syntax for creating such links is simple: just wrap the name of
any collection entry as in `[NAME]()`. For example, to create a link
to the documentation for the PERSON type, use

    [PERSON]()

which gives the following link

[PERSON]()

Alternatively, you can use empty HTML anchor tags (`<a>`, `</a>`),
as in

    <a>PERSON</a>

(These two alternative forms result in identical links.)

For cases where the same label (name) occurs in several collections,
it is possible to disambiguate the target by including the collection
name in the format `COLLECTION/ENTRY`, for example

    [entity/PERSON]()

(or, equivalently, `<a>entity/PERSON</a>`) which produces

[entity/PERSON]()

(Note that the text of the generated link only includes the entry
label.)

Either of these forms can be used in running text, for example

    [FAMILY]() relation arguments have type [PERSON]().

gives

[FAMILY]() relation arguments have type [PERSON]().

Cases where linking failed are visually marked to identify the
issue:

    [no-such-type]()

is shown as

[no-such-type]()

For all of the forms listed above, the text of the link matches the
linked type. To get a different text, use the syntax
`[text](TYPE)`. For example,

    [people](PERSON)

and 

    [people](entity/PERSON)

both generate the same link: [people](PERSON) and [people](entity/PERSON)

This form can also be written in HTML as

    <a href="PERSON">people</a>

Which again gives an identical link: <a href="PERSON">people</a>

Note that this automatic processing only applies to `<a>` elements
that have no `href`, `id`, or `name` attributes or whose `href`
attribute matches a simple pattern (e.g. lacking `http://` and
`.html`). This means that standard HTML anchors and links can be used
normally in Annodoc documents without triggering this feature.

## Configuration

Different aspects of the way a set of documentation is presented are
controlled by various configuration files and settings. The following
are the most important.

* `_config.yml`

The Jekyll top-level configuration file `_config.yml` controls many
aspects of the conversion of the source documents into the final site
as well as how Jekyll serves the site. This file also configures the
[collections](#collections) that are defined for the documentation.
Full documentation for `_config.yml` is available from
<http://jekyllrb.com/docs/configuration/>.

* `_includes/header.html`, `_includes/footer.html`

These HTML files are automatically attached to every page on the site.
Edit the HTML content of these two files to customize the look of the
documentation, add navigation, etc. These files are standard HTML.

* `css/main.css`, `css/style-vis.css`

The [CSS] files found in the `css` subdirectory control the style
(look) of the main documentation (`main.css`) and the visualizations
(`style-vis.css`). It is not necessary to modify these in basic
usage. If changes to the style of the documentation pages or the
visualization are needed, please refer to e.g.
<http://www.w3.org/Style/CSS/Overview.en.html> for more information.

* `lib/local/config.js`

This JavaScript file holds the configuration for the [brat]
visualization component. The configuration specifies, for example, the
colors, labels, label abbreviations, and line styles to use for
visualizing various categories of annotation. For documentation on the
contents and syntax of this file, refer to
<http://brat.nlplab.org/configuration.html>.

## Troubleshooting

The following sections provide instructions for troubleshooting
various possible issues with the system.

### Troubleshooting: basic visualization

Are the annotation visualizations working? To check, see if the following
visualization and image look (broadly) similar.

Visualization:

~~~ ann
Barack Obama is the current president.
T1 PERSON 0 12 Barack Obama
~~~

Image:

<img src="static/img/visualization-example.png">

If yes, the basic visualization support is OK. If no (e.g.  if instead
of a visualization text such as `T1 PERSON 0 12 Barack Obama` is
shown), then try the following:

* Make sure you are using a supported browser. The visualizations
  require [SVG] support.  We recommend recent versions of Chrome or
  Safari. For IE, version 9 or newer is required.

* Check that JavaScript is enabled. The system requires JavaScript to
  generate the visualizations and will fail without it.

* Check the JavaScript console for errors. (The console is accessed in
  different ways depending on your browser.)

* Check that coderay is not running on the server. If active, coderay
  may pre-empt embedded visualization processing by replacing the
  annotation blocks. The `_config.yml` option `kramdown:
  enable_coderay: false` should disable coderay.

* Report the issue to the developers: email `sampo.pyysalo@gmail.com`

### Troubleshooting: local usage

If you are having trouble running the system locally, please check
the following:

* Check that you have a recent version of Jekyll by running `jekyll -v`.
  Version 2.0 or greater is recommended.

Some debian-based linux distributions are currently shipping a dated
version of Jekyll. If you are using such a system, you may wish to
consider using `gem` instead of `apt-get` to install Jekyll (see e.g.
<http://jekyllrb.com/docs/installation/#install-with-rubygems>).

### Troubleshooting: editing online

If the "edit page" links do not appear on Annodoc documentation pages,
please make sure `editurl` site variable is set in `_config.yml` (see
[Configuration](#configuration)).

If the "edit page" link appears but does not lead to a GitHub
online editing page, please check the following:

* GitHub online editing is working as intended. Click on any document
in your GitHub repository and click on the pen icon to test this
feature.

* `editurl` is correctly set. Try comparing the generated "edit page"
links with the URL used for the GitHub online editing page.

* You are allowed to edit the repository (owner or collaborator) and
you are logged in to GitHub.

------------------------------------------------------------------------------

[Markdown]: http://daringfireball.net/projects/markdown/
[Stanford dependency]: http://nlp.stanford.edu/software/stanford-dependencies.shtml
[CoNLL-X]: http://ilk.uvt.nl/conll/#dataformat
[CoNLL-U]: http://universaldependencies.github.io/docs/format.html
[.ann standoff]: http://brat.nlplab.org/standoff.html
[SVG]: http://en.wikipedia.org/wiki/Scalable_Vector_Graphics
[Jekyll]: http://jekyllrb.com/
[brat]: http://brat.nlplab.org
[Liquid]: http://wiki.shopify.com/Liquid
[Git]: http://git-scm.com
[GitHub]: http://github.com
[Annodoc repository]: https://github.com/spyysalo/annodoc
[CSS]: http://en.wikipedia.org/wiki/Cascading_Style_Sheets
[YAML]: http://yaml.org/
