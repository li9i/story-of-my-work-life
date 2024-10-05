<!-- Slide 01 ------------------------------------------------------------- -->

```
01
I studied Electrical and Computer Engineering in the Aristotle University of
Thessaloniki, in Greece, from where I graduated in 2013.
```

<!-- Slide 02 ------------------------------------------------------------- -->

```
02
Immediately after I joined the department's undergraduate robotics team, called
PANDORA.  At that time PANDORA was developing autonomous UGVs and competing
once every two years in the international RoboCup Rescue robot league.
```

<!-- Slide 03 ------------------------------------------------------------- -->

```
03
This competition revolves around demonstrating capabilities for emergency
responders in catastrophic situations, and, in practice, the robot needed to
autonomously map a given environment, navigate in it, and locate simulated
victims, which were behind holes in walls. My task was to detect these kinds of
holes using RGB and Depth information.
```

<!-- Slide 04 ------------------------------------------------------------- -->

```
04
Here you can see the output of my ROS hydro package. My code had written tests
and documentation to the tune of 4000 lines in 8000 lines of code.
```

<!-- Slide 05 ------------------------------------------------------------- -->

```
05
Our team could not compete that year due to financial reasons, but the next
year it did, gaining second place in its class.
```

<!-- Slide 06 ------------------------------------------------------------- -->

```
06
My involvement in this team motivated me to want to educate myself on robotics,
so I applied to the master's program of Systems, Control, and Robotics of KTH,
where I was admitted in the fall of 2015.
```

<!-- Slide 07 ------------------------------------------------------------- -->

```
07
The Saturday before the Monday that classes would start they gathered us for an
introduction to the programme, and right of the bat they announced to us that
the term Robotics was clickbait, and that in essence we would mainly study
control.
```

<!-- Slide 08 ------------------------------------------------------------- -->

```
08
Passing through the programme I realised that they told us the truth, and I
eventually arrived on the third quarter of the programme, where my ROS skills
came in handy, and they combined with my new control education.
```

<!-- Slide 09 ------------------------------------------------------------- -->

```
09
In that quarter the major pre-degree project took place, and in our case
involved making a F1tenth vehicle track a circular trajectory, and also a
straight one through KTH's corridors. In this figures you can see the
trajectory during the transient phase. Eventually the tracking position error
would not exceed four centimeters at 50 cm/h speeds.
```

<!-- Slide 10 ------------------------------------------------------------- -->

```
10
Immediately after our pre-degree project came time to select a thesis. I very
much liked the course they offered us on MPC, so I gravitated towards using it
to control the state of multi-agent systems in a decentralised manner, and come
up with suitable control laws that would deal with state disturbances.
```

<!-- Slide 11 ------------------------------------------------------------- -->

```
11
More specifically the objective was to navigate and stabilise N agents while
avoiding obstacles in the environment, avoiding each other, and keeping
connectivity with each other, all while trying to attenuate disturbances.
```

<!-- Slide 12 ------------------------------------------------------------- -->

```
12
This was the end result. In the top figure you can see the three agents on the
left with colours other than black, obstacles in the environment with black, and
in the right-hand side the points where the agents should stabilise themselves.
As you can see the control framework provided did not violate the set distance
between agents, and also acted within the motors' capacities.
```

<!-- Slide 13 ------------------------------------------------------------- -->

```
13
In this figure you can see the agents' energy at the equilibrium points in the
case of no disturbances on the right hand side, and in the middle the case
where there are unaddressed disturbances. In the right-hand side you can see
that the provided control law guarantees that the energy of each agent is
bounded below a known threshold.
```

<!-- Slide 14 ------------------------------------------------------------- -->

```
14
These findings, along with a condensed version of the 30-page stability proof,
we published in the International Journal of Control in 2017.
```

<!-- Slide 15 ------------------------------------------------------------- -->

```
15
My achievements from this period were that I completed these very hard studies,
that my thesis is still getting hits after 7 years, and that our paper has
now 40 citations.
```

<!-- Slide 16 ------------------------------------------------------------- -->

```
16
After I received my degree I returned to Greece and in September of 2018 I
began to work for the university I graduated from as a freelance robotics
engineer.  During this 5-year period I worked on two research projects, I
started and received my PhD, and I authored six papers. But let's take things
from the beginning.
```

<!-- Slide 17 ------------------------------------------------------------- -->

```
17
I started work on project RELIEF, whose aim was to provide large warehouses
with the ability of 247 autonomous inventorying and accurate product
localisation via RFID and ground and aerial robots.
```

<!-- Slide 18 ------------------------------------------------------------- -->

```
18
In the left-hand side you can see one final ground robot we developed, standing
next to some supermarket products that were pre-tagged with RFID tags. In the
right-hand side you can see an RVIz depiction of the estimates of the products'
locations.
```

<!-- Slide 19 ------------------------------------------------------------- -->

```
19
In the beginning I did research on the autonomous navigation part of ground
robots that we would need for the project, which led to my first publication
during that period.
```

<!-- Slide 20 ------------------------------------------------------------- -->

```
20
In essence we set up an evaluation method and performed extensive experiments
in simulation in ROS, in Gazebo with a turtlebot, and in real conditions with a
Robotnik RB1, between local and global planners that were available then in
ROS. The experimental procedure followed a qualitative approach that sifted
packages based on software engineering theoretic and practical criteria.
```

<!-- Slide 21 ------------------------------------------------------------- -->

```
21
While conducting the experimental procedure and while compiling the results the
entire evaluation I noticed the existence of pose estimate errors, coming from
the observation of the robot's pose while using a LIDAR sensor, from the
particle filter we used to track its trajectory.
```

<!-- Slide 22 ------------------------------------------------------------- -->

```
22
Upon seeing this effect I understood that for the RELIEF project these errors
would mean trouble, as the product location estimate is based on the RFID
antennas' estimate, which in turn are based on the robot's pose estimate. So
I started researching how it would be possible to decrease the pose estimate
error by using LIDAR measurements while tracking with a particle filter.
```

<!-- Slide 23 ------------------------------------------------------------- -->

```
23
Eventually I implemented three ways to do so. The first one was novel and
had to do with the composition of the set of poses selected for voting towards
the final pose estimate, and more specifically with selecting poses based on
their weight. One of my findings is that, counterintuitively, the
pose with the hightest weight does not record the least error.
```

<!-- Slide 24 ------------------------------------------------------------- -->

```
24
The second implementation is actually the start point of my later dissertation.
As you can see in the left-hand side figure our initial configuration is that
typically we are given a map, a LIDAR measurement, and a pose estimate of the
pose from which the measurement was made. The problem here is to decrease the
pose estimate error. The function of the technique I encountered in the
literature is that first it captures a virtual scan from the pose estimate
withing the map, exactly analogously to how the real sensor captures a real
scan from its real pose. Then the second step is to register this map-scan on
the real scan. This registration produces the transform which, when applied to
the pose estimate, makes it in principle coincide with the LIDAR's true pose.
Before I came to the land of this technique, it didn't have a name, so in the
interest of the huge importance I believed it would be capable of having, and
in consistency with previous namings, I aptly named this technique
scan--to--map-scan matching.
```

<!-- Slide 25 ------------------------------------------------------------- -->

```
25
The third and final implementation was, as the first one, novel, and had to do
with the way that the scan--to--map-scan matched pose estimate could be fed
back to the population of the filter so that it progressively converged to
solutions with decreased errors.
```

<!-- Slide 26 ------------------------------------------------------------- -->

```
26
The experimental procedure of our contributions again was extensive. It
consisted in using a turtlebot robot in ROS in gazebo navigating autonomously in
simple and complex warehouse-like environments, with a noisy sensor, and
evaluating pose estimate errors along the robot's trajectory. In this case we
could not use a real robot because in our department we do not have motion
capturing systems that could record the ground truth pose.
```

<!-- Slide 27 ------------------------------------------------------------- -->

```
27
Our findings were published again in the Journal of Intelligent and Robotic
Systems a few months before COVID hit.
```

<!-- Slide 28 ------------------------------------------------------------- -->

```
28
In the mean time, in my spare time I was studying this paper that I found,
which had to do again with decreasing the position estimate of panoramic 2D
LIDAR sensors. I was fascinated with the ingenuity of the approach because it
employed the Fourier transform and because it showed just how much you could
decrease the error if you set up a control system that stabilised the position
estimate in a specific way. Although the authors setup a control system to
stabilise the estimate, and they showed their findings, they didn't provide any
proofs, so given that I learned how to do just that in my KTH thesis, I
provided this proof, and setup the code in C++ to test it against the state of
the art algorithms in scan-matching.
```

<!-- Slide 29 ------------------------------------------------------------- -->

```
29
Subsequently I wrote a paper on and submitted it in the beginning of January.
Later it was accepted in the Robotics and Autonomous Systems journal.
```

<!-- Slide 30 ------------------------------------------------------------- -->

```
30
About one year after I started work in the RELIEF project, its coordinator
approached me and proposed to me to do a PhD together. Eventually I said yes,
and continued to work on the project, while doing my research on my
own. This I continued for more than 3 years, and I was working
feverishly for 15 hours a day.
```

<!-- Slide 31 ------------------------------------------------------------- -->

```
31
During the setting up of the experimental procedure for the last two papers I
talked to you about, I integrated the best scan-matching algorithm of the then
literature. In working with, and by trying to make it give its best
performance, I witnessed that its solutions were very sensitive to its
multitude of parameters that you needed to tune, and to noise. In this case
noise comes either directly from the measurement, or from the imperfection of
the map. In the final analysis, these failings may altogether be attributed to
the nature of matching itself, which is done by locating correspondences of
points or lines between the input scans. So my next step is now to continue on
my path by constructing a method that matches panoramic scans in a
correspondenceless manner, not only when there is position error, but also when
there is orientation error as well.
```

<!-- Slide 32 ------------------------------------------------------------- -->

```
32
I research the literature high and low and come across the FMI-SPOMF method from
the field of machine vision, which can align two 2d-grids using closed-form
solutions, without establishing correspondences. The idea here is to turn the
scans into images first, match them in the image domain, and then return to the
original domain. Since we are talking about images, all the implementations I
tested could not yield an execution time compatible with the time between pose
updates by a typical filter. So I headed towards solving the localisation problem
with scan--to--map-scan matching without correspondences in principle, by
solving the global localisation problem.
```

<!-- Slide 33 ------------------------------------------------------------- -->

```
33
Again we tested this extensively, in ROS, both in gazebo an in real conditions, in
diverse environments with different sensor noise levels, and ...
```

<!-- Slide 34 ------------------------------------------------------------- -->

```
34
... our method was published again in the Journal of Intelligent and Robotic
Systems.
```

<!-- Slide 35 ------------------------------------------------------------- -->

```
35
Now, since we had surrounded the problem of decreasing the pose estimate error
with the use of correspondenceless scan--to--map-scan matching, it was time to
attack it so that it could be used during pose tracking, and that meant the
construction of real-time methods, meaning methods that could be executed in
less than 200ms.
```

<!-- Slide 36 ------------------------------------------------------------- -->

```
36
In the end I came up with three methods in total, all using the translation
component of my own paper, and each using separate rotational components, and
all running in what is considered in this kind of problem real-time. In doing
so we constructed the first ever full-blown real-time methods of
scan--to--map-scan matching without correspondences, which meant that they were
by design more robust to noise, the initial pose estimate errors, and that they
demanded far fewer parameters to tune than those of the state of the art.  I
would also say that my biggest contribution was the discovery of the Cumulative
Absolute Error per Ray metric, into which I will delve more later on.
```

<!-- Slide 37 ------------------------------------------------------------- -->

```
37
In this figure you can see the results of the experimental procedure, which
examined six state of the art methods, in over 45 thousand environments and 100
iterations. With black you see the state of art, and in shades of magenta my
three methods. This figure answers the following question: if I apply each
method to one hundred pose estimates, how many of them would end up with pose
errors less than the original? Here we consider two map distortion levels,
which you can see in the y-axis, and five levels of sensor noise, which
are levels that commercial sensors exhibit.
```

<!-- Slide 38 ------------------------------------------------------------- -->

```
38
We tried to publish the first method in the Robotics and Autonomous Systems
journal but they transferred our submission to a newly-introduced journal
called Array, in which it was later published.
```

<!-- Slide 39 ------------------------------------------------------------- -->

```
39
Once I solved the scan--to--map-scan matching problem I figured that if we
substituted the map for the 2d projection of another scan, then we could solve
the scan-matching problem, and in that way we could produce lidar odometry.
```

<!-- Slide 40 ------------------------------------------------------------- -->

```
40
In actual fact we produced the first ever correspondenceless method of
scan-matching which runs in real time, which meant that this way was more
robust to sensor noise and distances between two poses, and it needed less
parameters to tune, all problems inherent in one way or another to the state of
the art methods, which match scans by establishing correspondences between
them.
```

<!-- Slide 41 ------------------------------------------------------------- -->

```
41
In the experimental procedure I again considered noise levels exhibited by
commercially available sensors, five state of the real-time art algorithms,
over 45 thousand environments, ten iterations in each environment,
and varying radial and angular distances between two consecutive
sensor poses. It's difficult to see in this figure but the method I came up
with is better than all of the other methods in terms of median and mean
errors, except for two cases when noise is at its minimum.
```

<!-- Slide 42 ------------------------------------------------------------- -->

```
42
In this figure we see the difference in lidar odometry between the best
scan-matching algorithm, called plicp, and fsm, which the algorithm we built,
in real conditions with a real sensor. In this case, where there is no map,
and estimation is open-loop, you can see that plicp's pose estimates may go
through walls, but fsm exhibits better performance.
```

<!-- Slide 43 ------------------------------------------------------------- -->

```
43
We published fsm in IROS in 2022, along with its C++ code and its ROS wrapper.
```

<!-- Slide 44 ------------------------------------------------------------- -->

```
44
In June of the last year I defended my PhD thesis, after two months I joined
the Center for Research and Technology, here in Greece, where I currently work
as a postdoctoral research associate.
```

<!-- Slide 45 ------------------------------------------------------------- -->

```
45
For the past year I have led our group's efforts in transitioning from ROS 1
to ROS 2, and I have been working in a European-Commission-funded project, which
has resulted in my using Behavior Trees in ROS 2 for task planning purposes,
and also in integration work, which means developing and deploying with Docker
containers, and also bridging ROS 1 and ROS 2, as well as different machines.
```

<!-- Slide 46 ------------------------------------------------------------- -->

```
46
The second-to-last thing I want to talk to you about is that I have continued
the work in my PhD by creating a global localisation method for 2d lidar
sensors, that is a method that given the map of an environment and a single
measurement, estimates the pose of the sensor quickly. As I told you earlier I
consider the discovery of the Cumulative Absolute Error per Ray metric perhaps
the greatest contribution of my work, because, if you notice at the right-hand
side figure, you will see that for pose estimates in a neighbourhood of the
true pose of a lidar sensor, their CAER metric is proportional to their
position error and also their orientation error as well. Which means that if we
disperse enough pose hypotheses on the map then we may estimate the pose of the
sensor quickly due to the low computational complexity of the metric.
```

<!-- Slide 47 ------------------------------------------------------------- -->

```
47
These are the results of the experimental procedure in real conditions, under
ROS 1, in the Computer Systems Architecture lab of university i got my phd
from. Here we see that CBGL was inputted more than six and a half thousand
measurements and estimated the pose of the sensor with a position error less
than half a meter more than 99 per cent of the time. Its mean execution time
was one point six seconds, while in other experiments it was revealed that its
execution time is one second per one hundred meters squared of environment area.
```

<!-- Slide 48 ------------------------------------------------------------- -->

```
48
CBGL was accepted in IROS of 2024, and I will be traveling to Abu Dhabi to
present the method.
```

<!-- Slide 49 ------------------------------------------------------------- -->

```
49
Now these are my goals for the next years. I would like to find a team to work
with, and learn from, and expand my knowledge and my skills on the implementation
side of things. Right now I am in the unfortunate position where I am not
appreciated where I work, and that is the reason I want to leave CERTH. I also
have grown tired of working too much and under the conditions I am working in
so I would like to be less stressed and work fewer hours. Lastly I would like to
focus more on the implementation side as I've told you, and leave the process of
writing papers because my ideas and their presentation have been met by my
peers with disproportionately high strictness and comments that reveal the abuse
they have endured in their career.
```

<!-- Slide 50 ------------------------------------------------------------- -->

```
50
And finally these are my questions to you, which we can discuss later on. Thank
you for your time and for your attention.
```
