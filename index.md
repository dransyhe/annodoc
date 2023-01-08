---
layout: entry
title: Grammatical Relations Results
---

1\. My aunt's can opener can open a drum.  

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

~~~ conllu
1 My my PRP$ PRP$ _ 2 nmod:poss _ _
2 aunt aunt NN NN _ 5 nmod:poss _ _
3 's 's POS POS _ 2 case _ _
4 can can NN NN _ 5 compound _ _
5 opener opener NN NN _ 7 nsubj _ _
6 can can MD MD _ 7 aux _ _
7 open open VB VB _ 0 root _ _
8 a a DT DT _ 9 det _ _
9 drum drum NN NN _ 7 obj _ _
10 . . . . _ 7 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
My/PRP$ aunt/NN 's/POS can/MD opener/NN can/MD open/VB a/DT drum/NN ./.
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

2\. The old car broke down in the car park.  

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

~~~ conllu
1 The the DT DT _ 3 det _ _
2 old old JJ JJ _ 3 amod _ _
3 car car NN NN _ 4 nsubj _ _
4 broke break VBD VBD _ 0 root _ _
5 down down RP RP _ 4 compound:prt _ _
6 in in IN IN _ 9 case _ _
7 the the DT DT _ 9 det _ _
8 car car NN NN _ 9 compound _ _
9 park park NN NN _ 4 obl _ _
10 . . . . _ 4 punct _ _

~~~

- NN-based dependency parser:

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
obl(broke-4, park-9)
punct(broke-4, .-10)
~~~

3\. At least two men broke in and stole my TV.  

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

~~~ conllu
1 At at IN IN _ 2 case _ _
2 least least JJS JJS _ 3 obl:npmod _ _
3 two two CD CD _ 4 nummod _ _
4 men man NNS NNS _ 5 nsubj _ _
5 broke break VBD VBD _ 0 root _ _
6 in in RP RP _ 5 compound:prt _ _
7 and and CC CC _ 8 cc _ _
8 stole steal VBD VBD _ 5 conj _ _
9 my my PRP$ PRP$ _ 10 nmod:poss _ _
10 TV tv NN NN _ 8 obj _ _
11 . . . . _ 5 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
At/RB least/RBS two/CD men/NNS broke/VBD in/IN and/CC stole/VBD my/PRP$ TV/NN ./.
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

4\. Kim and Sandy both broke up with their partners.  

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

~~~ conllu
1 Kim Kim NNP NNP _ 5 nsubj _ _
2 and and CC CC _ 3 cc _ _
3 Sandy Sandy NNP NNP _ 1 conj _ _
4 both both DT DT _ 5 dep _ _
5 broke break VBD VBD _ 0 root _ _
6 up up RP RP _ 5 compound:prt _ _
7 with with IN IN _ 9 case _ _
8 their they PRP$ PRP$ _ 9 nmod:poss _ _
9 partners partner NNS NNS _ 5 obl _ _
10 . . . . _ 5 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
Kim/NNP and/CC Sandy/NNP both/CC broke/VBD up/RP with/IN their/PRP$ partners/NNS ./.
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


5\. The horse as well as the rabbits which we wanted to eat has escaped.  

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

~~~ conllu
1 The the DT DT _ 2 det _ _
2 horse horse NN NN _ 14 nsubj _ _
3 as as RB RB _ 7 cc _ _
4 well well RB RB _ 3 fixed _ _
5 as as IN IN _ 3 fixed _ _
6 the the DT DT _ 7 det _ _
7 rabbits rabbit NNS NNS _ 2 conj _ _
8 which which WDT WDT _ 10 obj _ _
9 we we PRP PRP _ 10 nsubj _ _
10 wanted want VBD VBD _ 7 acl:relcl _ _
11 to to TO TO _ 12 mark _ _
12 eat eat VB VB _ 10 xcomp _ _
13 has have VBZ VBZ _ 14 aux _ _
14 escaped escape VBN VBN _ 0 root _ _
15 . . . . _ 14 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
The/DT horse/NN as/RB well/RB as/IN the/DT rabbits/NNS which/WDT we/PRP wanted/VBD to/TO eat/VB has/VBZ escaped/VBN ./.
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

6\. It was my aunt's car which we sold at auction last year in February.  

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

~~~ conllu
1 It it PRP PRP _ 6 nsubj _ _
2 was be VBD VBD _ 6 cop _ _
3 my my PRP$ PRP$ _ 4 nmod:poss _ _
4 aunt aunt NN NN _ 6 nmod:poss _ _
5 's 's POS POS _ 4 case _ _
6 car car NN NN _ 0 root _ _
7 which which WDT WDT _ 9 obj _ _
8 we we PRP PRP _ 9 nsubj _ _
9 sold sell VBD VBD _ 6 acl:relcl _ _
10 at at IN IN _ 11 case _ _
11 auction auction NN NN _ 9 obl _ _
12 last last JJ JJ _ 13 amod _ _
13 year year NN NN _ 9 obl:tmod _ _
14 in in IN IN _ 15 case _ _
15 February February NNP NNP _ 9 obl _ _
16 . . . . _ 6 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
It/PRP was/VBD my/PRP$ aunt/NN 's/POS car/NN which/WDT we/PRP sold/VBD at/IN auction/NN last/JJ year/NN in/IN February/NNP ./.
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

7\. Natural disasters – storms, flooding, hurricanes – occur infrequently but cause devastation that strains resources to breaking point.  

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

~~~ conllu
1 Natural natural JJ JJ _ 2 amod _ _
2 disasters disaster NNS NNS _ 0 root _ _
3 – – SYM SYM _ 4 dep _ _
4 storms storm NNS NNS _ 2 nmod _ _
5 , , , , _ 2 punct _ _
6 flooding flooding NN NN _ 2 appos _ _
7 , , , , _ 2 punct _ _
8 hurricanes hurricane NNS NNS _ 2 appos _ _
9 – – : : _ 2 punct _ _
10 occur occur VB VB _ 2 dep _ _
11 infrequently infrequently RB RB _ 10 advmod _ _
12 but but CC CC _ 13 cc _ _
13 cause cause VB VB _ 10 conj _ _
14 devastation devastation NN NN _ 13 obj _ _
15 that that WDT WDT _ 16 nsubj _ _
16 strains strain VBZ VBZ _ 14 acl:relcl _ _
17 resources resource NNS NNS _ 16 obj _ _
18 to to IN IN _ 19 mark _ _
19 breaking break VBG VBG _ 16 advcl _ _
20 point point NN NN _ 19 obj _ _
21 . . . . _ 2 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
Natural/JJ disasters/NNS –/SYM storms/NNS ,/, flooding/NN ,/, hurricanes/NNS –/SYM occur/VBP infrequently/RB but/CC cause/VB devastation/NN that/IN strains/NNS resources/NNS to/IN breaking/VBG point/NN ./.
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

8\. Letters delivered on time by old-fashioned means are increasingly rare, so it is as well that that is not the only option available.  

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

~~~ conllu
1 Letters Letters NNPS NNPS _ 12 nsubj _ _
2 delivered deliver VBN VBN _ 1 acl _ _
3 on on IN IN _ 4 case _ _
4 time time NN NN _ 2 obl _ _
5 by by IN IN _ 9 case _ _
6 old old JJ JJ _ 8 amod _ _
7 - - HYPH HYPH _ 8 punct _ _
8 fashioned fashioned JJ JJ _ 9 amod _ _
9 means means NNS NNS _ 2 obl _ _
10 are be VBP VBP _ 12 cop _ _
11 increasingly increasingly RB RB _ 12 advmod _ _
12 rare rare JJ JJ _ 0 root _ _
13 , , , , _ 12 punct _ _
14 so so IN IN _ 16 mark _ _
15 it it PRP PRP _ 16 nsubj _ _
16 is be VBZ VBZ _ 12 advcl _ _
17 as as RB RB _ 16 advmod _ _
18 well well RB RB _ 17 fixed _ _
19 that that IN IN _ 26 mark _ _
20 that that DT DT _ 26 nsubj _ _
21 is be VBZ VBZ _ 26 cop _ _
22 not not RB RB _ 26 advmod _ _
23 the the DT DT _ 25 det _ _
24 only only JJ JJ _ 25 amod _ _
25 option option NN NN _ 26 obl:npmod _ _
26 available available JJ JJ _ 17 advcl _ _
27 . . . . _ 12 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
Letters/NNPS delivered/VBD on/IN time/NN by/IN old/JJ -/HYPH fashioned/JJ means/NNS are/VBP increasingly/RB rare/JJ ,/, so/IN it/PRP is/VBZ as/RB well/RB that/IN that/DT is/VBZ not/RB the/DT only/JJ option/NN available/JJ ./.
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

9\. English also has many words of more or less unique function, including interjections (oh, ah), negatives (no, not), politeness markers (please, thank you), and the existential 'there' (there are horses but not unicorns) among others.  

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

~~~ conllu
1 English English NNP NNP _ 3 nsubj _ _
2 also also RB RB _ 3 advmod _ _
3 has have VBZ VBZ _ 0 root _ _
4 many many JJ JJ _ 5 amod _ _
5 words word NNS NNS _ 3 obj _ _
6 of of IN IN _ 11 case _ _
7 more more RBR RBR _ 10 advmod _ _
8 or or CC CC _ 9 cc _ _
9 less less RBR RBR _ 7 conj _ _
10 unique unique JJ JJ _ 11 amod _ _
11 function function NN NN _ 5 nmod _ _
12 , , , , _ 11 punct _ _
13 including include VBG VBG _ 14 case _ _
14 interjections interjection NNS NNS _ 11 nmod _ _
15 ( ( -LRB- -LRB- _ 16 punct _ _
16 oh oh CD CD _ 14 dep _ _
17 , , , , _ 16 punct _ _
18 ah ah JJ JJ _ 16 dep _ _
19 ) ) -RRB- -RRB- _ 16 punct _ _
20 , , , , _ 14 punct _ _
21 negatives negative NNS NNS _ 14 conj _ _
22 ( ( -LRB- -LRB- _ 21 punct _ _
23 no no UH UH _ 25 discourse _ _
24 , , , , _ 25 punct _ _
25 not not RB RB _ 21 dep _ _
26 ) ) -RRB- -RRB- _ 21 punct _ _
27 , , , , _ 14 punct _ _
28 politeness politeness JJ JJ _ 29 amod _ _
29 markers marker NNS NNS _ 14 conj _ _
30 ( ( -LRB- -LRB- _ 29 punct _ _
31 please please UH UH _ 34 discourse _ _
32 , , , , _ 31 punct _ _
33 thank thank UH UH _ 31 dep _ _
34 you you PRP PRP _ 29 dep _ _
35 ) ) -RRB- -RRB- _ 29 punct _ _
36 , , , , _ 14 punct _ _
37 and and CC CC _ 41 cc _ _
38 the the DT DT _ 41 det _ _
39 existential existential JJ JJ _ 41 amod _ _
40 ' ' `` `` _ 41 punct _ _
41 there there RB RB _ 14 conj _ _
42 ' ' '' '' _ 41 punct _ _
43 ( ( -LRB- -LRB- _ 45 punct _ _
44 there there EX EX _ 45 expl _ _
45 are be VBP VBP _ 5 dep _ _
46 horses horse NNS NNS _ 45 nsubj _ _
47 but but CC CC _ 48 cc _ _
48 not not RB RB _ 49 cc _ _
49 unicorns unicorn NNS NNS _ 46 conj _ _
50 ) ) -RRB- -RRB- _ 45 punct _ _
51 among among IN IN _ 52 case _ _
52 others other NNS NNS _ 5 nmod _ _
53 . . . . _ 3 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
English/NNP also/RB has/VBZ many/JJ words/NNS of/IN more/RBR or/CC less/RBR unique/JJ function/NN ,/, including/VBG interjections/NNS (/-LRB- oh/UH ,/, ah/UH )/-RRB- ,/, negatives/NNS (/-LRB- no/UH ,/, not/RB )/-RRB- ,/, politeness/NN markers/NNS (/-LRB- please/UH ,/, thank/VBP you/PRP )/-RRB- ,/, and/CC the/DT existential/JJ '/`` there/EX '/'' (/-LRB- there/EX are/VBP horses/NNS but/CC not/RB unicorns/NNS )/-RRB- among/IN others/NNS ./.
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

~~~ conllu
1 The the DT DT _ 4 det _ _
2 Penn Penn NNP NNP _ 4 compound _ _
3 Treebank Treebank NNP NNP _ 4 compound _ _
4 tagset tagset NNP NNP _ 6 nsubj:pass _ _
5 was be VBD VBD _ 6 aux:pass _ _
6 culled cull VBN VBN _ 0 root _ _
7 from from IN IN _ 13 case _ _
8 the the DT DT _ 13 det _ _
9 original original JJ JJ _ 13 amod _ _
10 87 87 CD CD _ 12 nummod _ _
11 - - HYPH HYPH _ 12 punct _ _
12 tag tag NN NN _ 13 compound _ _
13 tagset tagset NN NN _ 6 obl _ _
14 for for IN IN _ 17 case _ _
15 the the DT DT _ 17 det _ _
16 Brown Brown NNP NNP _ 17 compound _ _
17 Corpus Corpus NNP NNP _ 13 nmod _ _
18 . . . . _ 6 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
The/DT Penn/NNP Treebank/NNP tagset/NN was/VBD culled/VBN from/IN the/DT original/JJ 87/CD -/HYPH tag/NN tagset/NN for/IN the/DT Brown/NNP Corpus/NNP ./.
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

~~~ conllu
1 For for IN IN _ 2 case _ _
2 example example NN NN _ 9 obl _ _
3 the the DT DT _ 8 det _ _
4 original original JJ JJ _ 8 amod _ _
5 Brown Brown NNP NNP _ 8 compound _ _
6 and and CC CC _ 7 cc _ _
7 C5 C5 NNP NNP _ 5 conj _ _
8 tagsets tagset NNS NNS _ 9 nsubj _ _
9 include include VBP VBP _ 0 root _ _
10 a a DT DT _ 12 det _ _
11 separate separate JJ JJ _ 12 amod _ _
12 tag tag NN NN _ 22 nsubj _ _
13 for for IN IN _ 14 case _ _
14 each each DT DT _ 12 nmod _ _
15 of of IN IN _ 18 case _ _
16 the the DT DT _ 18 det _ _
17 different different JJ JJ _ 18 amod _ _
18 forms form NNS NNS _ 14 nmod _ _
19 of of IN IN _ 21 case _ _
20 the the DT DT _ 21 det _ _
21 verbs verb NNS NNS _ 18 nmod _ _
22 do do VB VB _ 9 ccomp _ _
23 ( ( -LRB- -LRB- _ 27 punct _ _
24 e.g. e.g. FW FW _ 27 dep _ _
25 C5 C5 NNP NNP _ 27 compound _ _
26 tag tag NNP NNP _ 27 compound _ _
27 VDD VDD NNP NNP _ 22 dep _ _
28 for for IN IN _ 29 mark _ _
29 did do VBD VBD _ 27 dep _ _
30 and and CC CC _ 31 cc _ _
31 VDG vdg VBD VBD _ 29 conj _ _
32 tag tag NN NN _ 29 obj _ _
33 for for IN IN _ 34 mark _ _
34 doing do VBG VBG _ 29 advcl _ _
35 ) ) -RRB- -RRB- _ 27 punct _ _
36 , , , , _ 22 punct _ _
37 be be VB VB _ 22 conj _ _
38 and and CC CC _ 39 cc _ _
39 have have VB VB _ 22 conj _ _
40 . . . . _ 9 punct _ _

~~~

- NN-based dependency parser:

~~~ sdparse
For/IN example/NN the/DT original/JJ Brown/NNP and/CC C5/NN tagsets/NNS include/VBP a/DT separate/JJ tag/NN for/IN each/DT of/IN the/DT different/JJ forms/NNS of/IN the/DT verbs/NNS do/VBP (/-LRB- e.g./FW C5/NN tag/NN VDD/NN for/IN did/VBD and/CC VDG/NNP tag/NN for/IN doing/VBG )/-RRB- ,/, be/VB and/CC have/VB ./.
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

