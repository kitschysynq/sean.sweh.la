+++
title = "Woodworking for Nerds"
date = "2020-05-06T16:24:21-04:00"
author = "thor"
authorTwitter = "kitschysynq"
cover = ""
tags = ["woodworking", "math"]
keywords = ["", ""]
description = "I'm always a sucker for a good math problem, doubly so when there are power tools involved."
showFullContent = false
+++

A friend recently asked if I was interested in "a woodworking 'problem' involving math." I
couldn't help but take that kind of bait, and he continued with a picture:

{{< image src="crossmember.jpg" alt="Photo of the end of a wooden table" position="center" style="border-radius: 8px;" >}}

and a simple question: How do you find the cut angles and length of these cross members?

This ought to be relatively simple geometry but it's been a while since I've thought about a problem
quite like this, so it took me a few tries to work it out fully. My friend had
worked out the solution in a spreadsheet, so we were able to compare notes while
I worked toward a solution. Here's a diagram we used for reference:

{{< image src="diagram.png" alt="Diagram of layout highlights" position="center" style="border-radius: 8px;" >}}

Starting from this diagram, we assume that we'll know the measurement for width
(which we'll call $w_o$ as in "width of the opening"), and for height (which
we'll similarly call $h_o$). We'll also know the width of the crossmember,
which isn't well marked in this diagram. Let's call that $w_c$. So the
measurements we're after are $\angle{EBD}$ and the length of $\overline{BE}$.
Let's call that angle $\theta_{cut}$, and the length $l$.

It doesn't seem as though either of these is simple to calculate directly, so I
started to look at what I _could_ calculate directly. The easiest seems to be
the hypotenuse of the opening, $\overline{BC}$. This is just plugging into the
pythagorean theorem:

$$
\begin{equation}
  \overline{BC} = \sqrt{{w_o}^2+{h_o}^2}
\end{equation}
$$

I want to calculate $\angle{EBD}$, and I still don't think I have enough
information to do that. It looks like $\angle{CBD}$ is a hefty part of that,
though, and I _do_ have enough information to calculate that using the sin law
of triangles:

$$
\begin{equation}
  {h_o \over sin{\left \(\angle{CBD}\right \)}} = {\overline{BE} \over sin{\left \(90\right \)}}
\end{equation}
$$
$$
\begin{equation}
  {h_o \over sin{\left \(\angle{CBD}\right \)}} = {\overline{BE} \over 1}
\end{equation}
$$
$$
\begin{equation}
  {h_o \over sin{\left \(\angle{CBD}\right \)}} = \overline{BE}
\end{equation}
$$
$$
\begin{equation}
  {sin{\left \(\angle{CBD}\right \)}} = {{h_o} \over \overline{BE}}
\end{equation}
$$
$$
\begin{equation}
  \angle{CBD} = arcsin{\left \({h_o} \over \overline{BE}\right \)}
\end{equation}
$$

and just to keep things as close as reasonable to the original set of known measurements:

$$
\begin{equation}
  \angle{CBD} = arcsin{\left \({h_o} \over \sqrt{{w_o}^2+{h_o}^2}\right \)}
\end{equation}
$$

Now I know $\angle{CBD}$ but that's only part of the angle that I need. More specifically I know that

$$ \angle{EBD} = \angle{EBC} + \angle{CBD} $$

If I can figure out $\angle{EBC}$, then, I can figure out $\theta_{cut}$. I can
construct a right triangle within the crossmember using $\overline{BE}$ and
$W_c$. At this point I can use the sin law again on this new right triangle:

$$
\begin{equation}
  {\overline{BE} \over sin{\left \(90\right \)}} = {w_c \over sin{\left \(\angle{EBC}\right \)}}
\end{equation}
$$
$$
\begin{equation}
  {sin{\left \(\angle{EBC}\right \)} \over sin{\left \(90\right \)}} = {w_c \over \overline{BE}}
\end{equation}
$$
$$
\begin{equation}
  {sin{\left \(\angle{EBC}\right \)} \over 1} = {w_c \over \overline{BE}}
\end{equation}
$$
$$
\begin{equation}
  {\angle{EBC}} = arcsin{\left \(w_c \over \overline{BE}\right \)}
\end{equation}
$$

And substituting back in like before:
$$
\begin{equation}
  {\angle{EBC}} = arcsin{\left \(w_c \over \sqrt{{w_o}^2+{h_o}^2}\right \)}
\end{equation}
$$

Since we have defined $\theta_{cut}$ as
$$
\begin{equation}
  \theta_{cut} = \angle{EBD}
\end{equation}
$$

 we've got the answer to the first part of our problem:

$$
\begin{equation}
  \theta_{cut} = \angle{EBC} + \angle{CBD}
\end{equation}
$$
$$
\begin{equation}
  \theta_{cut} = arcsin{\left \(w_c \over \sqrt{{w_o}^2+{h_o}^2}\right \)} + arcsin{\left \({h_o} \over \sqrt{{w_o}^2+{h_o}^2}\right \)}
\end{equation}
$$

Ok! I'm part way there. I know what to set the saw to, so I could make the
first cut. Now I need to figure out how far apart to make the cuts. For this,
I leaned on my friend sin law once again. I considered $\overline{BE}$ as one
side of $\triangle{BEC}$, so sin law gives me this relationship:

$$
\begin{equation}
  {\overline{BC} \over sin{\left \(\angle{BEC}\right \)}} = {\overline{BE} \over sin{\left \(\angle{BCE}\right \)}}
\end{equation}
$$

and solving that for $\angle{BE}$:

$$
\begin{equation}
  \overline{BE} = {{\overline{BC} \times sin{\left \(\angle{BCE}\right \)}} \over sin{\left \(\angle{BEC}\right \)}}
\end{equation}
$$

Since $\overline{BE}$ is a transversal of the parallel lines $\overline{BD}$ and $\overline{EC}$, it follows that
$$ \angle{BEC} = 180^{\circ} - \angle{EBD} $$
and
$$ \angle{BCE} = \angle{CBD} $$

Applying these to (16) gives:

$$
\begin{equation}
  \overline{BE} = {{\overline{BC} \times sin{\left \(\angle{CBD}\right \)}} \over sin{\left \(180^{\circ}-\angle{EBD}\right \)}}
\end{equation}
$$

Substituting values from (1), (7), and (13) simplifies this to

$$
\begin{equation}
  \overline{BE} = {{\sqrt{{w_o}^2+{h_o}^2} \times sin{\left \(arcsin{\left \({h_o \over \sqrt{{w_o}^2+{h_o}^2}}\right \)}\right \)}} \over sin{\left \(180^{\circ} - \theta_{cut}\right \)}}
\end{equation}
$$
$$
\begin{equation}
  \overline{BE} = {{\sqrt{{w_o}^2+{h_o}^2} \times {h_o \over \sqrt{{w_o}^2+{h_o}^2}}} \over sin{\left \(180^{\circ} - \theta_{cut}\right \)}}
\end{equation}
$$
$$
\begin{equation}
  \overline{BE} = {h_o \over sin{\left \(180^{\circ} - \theta_{cut}\right \)}}
\end{equation}
$$
$$
\begin{equation}
  l = {h_o \over sin{\left \(180^{\circ} - \theta_{cut}\right \)}}
\end{equation}
$$

And there we have it! Given $l$ and $\theta\_{cut}$ I could now get out the
speedsquare and circular saw and cut myself a crossmember. Oh, but one more
thing! What length of board would I need to cut the crossmember _from_?
Depending on how you look at it, this could also be the length that you'd set
a stop block when making the cuts. Let's call this measuremnt $l_{overall}$. It
turns out this is even easier to calculate than $l$. The first thing I
considered is that $l_{overall}$, $w_c$, and $\overline{BC}$ form a right
triangle. I drew a diagram to visualize but went a much lower-tech route than
my friend did with the diagram above.

{{< image src="diagram2.jpg" alt="Hand drawn diagram of the larger right triangle" position="center" style="border-radius: 8px;" >}}

Don't worry about the specific numbers here, or the extra labels (especially
that $\alpha$ - that never happened). Since I know the hypotenuse and the
height, I only need to calculate the base of this triangle. Plugging
everything into the pythagorean theorem, I get:

$$
\begin{equation}
  {l_{overall}}^2 + {w_c}^2 = \overline{BC}^2
\end{equation}
$$

which I can then solve for $l_{overall}$:

$$
\begin{equation}
  {l_{overall}}^2 = \overline{BC}^2 - {w_c}^2
\end{equation}
$$
$$
\begin{equation}
  {l_{overall}}^2 = \left \(\sqrt{{w_o}^2+{h_o}^2}\right \)^2 - {w_c}^2
\end{equation}
$$
$$
\begin{equation}
  {l_{overall}}^2 = {w_o}^2+{h_o}^2 - {w_c}^2
\end{equation}
$$
$$
\begin{equation}
  l_{overall} = \sqrt{{w_o}^2+{h_o}^2 - {w_c}^2}
\end{equation}
$$

And that's it! Now I can easily measure and cut, whichever way I'm thinking
about it. Now I just need to find an excuse to actually build this table...


To recap, the solution to the measurements I'd need to build the table are:

$$
\begin{equation}
  \theta_{cut} = arcsin{\left \(h_o \over \sqrt{{w_o}^2+{h_o}^2} \right \)} + arcsin{\left \( w_c \over \sqrt{{w_o}^2+{h_o}^2} \right \)}
\end{equation}
$$
$$
\begin{equation}
  l = {h \over sin(180 - \theta_{cut})}
\end{equation}
$$
$$
\begin{equation}
  l_{overall} = \sqrt{{w_o}^2+h^2-{w_c}^2}
\end{equation}
$$

---

Update: My friend also compiled a very nice spreadsheet to do these
calculations, which you can find [here](https://docs.google.com/spreadsheets/d/1JiPpa4Iv39l-C_cPjpzvj7IzMe3c0x1_53wzVHW7cF8/edit#gid=0).
It includes more complete diagrams, and the ability to round to a precision
that matches your equipment.
