# 18.337J/6.338J: Parallel Computing and Scientific Machine Learning

There are two main branches of technical computing: machine learning and
scientific computing. Machine learning has received a lot of hype over the
last decade, with techniques such as convolutional neural networks and TSne
nonlinear dimensional reductions powering a new generation of data-driven
analytics. On the other hand, many scientific disciplines carry on with
large-scale modeling through differential equation modeling, looking at
stochastic differential equations and partial differential equations describing
scientific laws.

However, there has been a recent convergence of the two disciplines. This field,
scientific machine learning, has been showcasing results like how partial
differential equation simulations can be accelerated with neural networks.
New methods, such as probabilistic and differentiable programming, have
started to be developed specifically for enhancing the tools of this domain.
However, the techniques in this field combine two huge areas of computational
and numerical practice, meaning that the methods are sufficiently complex.
How do you backpropogate an ODE defined by neural networks? How do you perform
unsupervised learning of a scientific simulator?

In this class we will dig into the methods and understand what they do, why
they were made, and thus how to integrate numerical methods across fields to
accentuate their pros while mitigating their cons. This class will be a survey
of the numerical techniques, showcasing how many disciplines are doing the
same thing under different names, and using a common mathematical language
to derive efficient routines which capture both data-driven and mechanistic-based
modeling.

However, these methods will quickly run into a scaling issue if naively coded.
To handle this problem, everything will have a focus on performance-engineering.
We will start by focusing on algorithm which are inherently serial and
learn to optimize serial code. Then we will showcase how logic-heavy
code can be parallelized through multithreading and distributed computing
techniques like MPI, while direct mathematical descriptions can be parallelized
through GPU computing.

The final part of the course will be a unique project which pulls together these
techniques. As a new field, the students will be exposed to the "low hanging
fruit" and will be directed towards an area which they can make a quick impact.
For the final project, students will team up to solve a new problem in the field of
scientific machine learning, and receive helping writing up a publication-quality
analysis about their work.

Syllabus
--------

**Lectures**: Monday/Wednesday 9:30-11am (4-163). **Office Hours:** Tuesday 12–2pm (32-G785, the Julia Lab).

**Prerequisites**: While this course will be mixing ideas from high performance
computing, numerical analysis, and machine learning, no one in the course is
expected to have covered all of these topics before. Understanding of calculus,
linear algebra, and programming is essential. 18.337 is a graduate-level
subject so mathematical maturity and the ability to learn from primary
literature is necessary. Problem sets will involve use of
[Julia](http://julialang.org/), a Matlab-like environment (little or no prior
experience required; you will learn as you go).

**Textbook & Other Reading**: There is no textbook for this course or the field
of scientific machine learning. Some helpful resources are
[Hairer and Wanner's Solving Ordinary Differential Equations I & II](https://www.springer.com/gp/book/9783540566700)
and [Gilbert Strang's Computational Science and Engineering](https://www.amazon.com/Computational-Science-Engineering-Gilbert-Strang/dp/0961408812).
Much of the reading will come in the form of primary literature from journal
articles posted here.

**Grading**: 66% problem sets, 34% **final project + presentation** due the last
day of class. Problem sets and final projects will be submitted electronically.

**Collaboration policy**: Make an effort to solve the problem on your own before
discussing with any classmates. When collaborating, write up the solution on
your own and acknowledge your collaborators.

**Final project**: The final project is a 10-20 page paper using the style
template from the [_SIAM Journal on Numerical Analysis_](http://www.siam.org/journals/auth-info.php)
(or similar), reviewing an interesting numerical algorithm not covered in
the course. The final project must include code for a parallelized implementation.
A thorough performance analysis is expected. Model your paper on academic
review articles (e.g. read _SIAM Review_ and similar journals for examples).
Some examples include:

- High performance PDE solvers
- Common high performance algorithms (Ex: Jacobian-Free Newton Krylov for PDEs)
- Recreation of a parameter sensitivity study
- Augmented Neural Ordinary Differential Equations
- Parallelized stencil calculations
- A multithreaded implementation of BLAS3
- Distributed linear algebra kernels

Additionally, Scientific Machine Learning is a wide open field with lots of
low hanging fruit. Instead of a review, a suitable research project can be
used for chosen for the final project. Possibilities include:

- Acceleration methods for adjoints of differential equations
- Improved methods for Physics-Informed Neural Networks
- New applications of neural differential equations
- Parallelized implicit ODE solvers for large ODE systems
- GPU-parallelized ODE/SDE solvers for small systems

Final project topics must be declared by October 11 with a 1 page extended
abstract.

## Schedule of Topics

Each topic is a group of three pieces: a numerical method, a performance-engineering
technique, and a scientific application. These three together form a complete
usable program that is demonstrated.

Homework 0: Using HPC Clusters

- The basics of scientific simulators (Week 1)
  - What is Scientific Machine Learning?
  - Optimization of serial code.
  - Introduction to discrete and continuous dynamical systems.
  - Ordinary differential equations as the language for ecology, Newtonian mechanics,
    and beyond.
  - Numerical methods for non-stiff ordinary differential equations
- Introduction to Parallel Computing (Week 2)
  - Tutorial on using the Supercloud HPC (Get an account setup!)
  - Forms of parallelism and applications
  - Parallelizing differential equation solvers
  - Optimal local parallelism via multithreading (Guest lecture: Alan Edelman)
  - Linear Algebra libraries you should know

Homework 1: Parallelized global sensitivity analysis of discrete and continuous
dynamical systems

- Stiffness of biological and chemical reaction systems (Week 2-3)
  - Definition of stiffness
  - Efficiently solving stiff ordinary differential equations
  - Stiff differential equations arising from biochemical interactions in developmental
    biology and ecology
  - Utilizing type systems and generic algorithms as a mathematical tool
  - Forward-mode automatic differentiation for solving f(x)=0
  - Matrix coloring and sparse differentiation
- Partial differential equations, neural networks, and array-based parallelism (Week 4-5)
  - Cache optimization in numerical linear algebra
  - Discretizations of PDEs
  - Basics of neural networks and definitions
  - The relationship between convolutional neural networks and PDEs
  - Parallelism through array operations
  - How to optimize algorithms for GPUs

Homework 2: Use Convolutional Neural Network Primitives to GPU-accelerate a
PDE solver

- Inverse problems and Differentiable Programming (Week 6)
  - Definition of inverse problems with applications to clinical pharmacology
    and smartgrid optimization
  - Adjoint methods for fast gradients
  - Automated adjoints through reverse-mode automatic differentiation (backpropogation)
- Physics-Informed Neural Networks and Neural Differential Equations (Week 6-7)
  - Adjoints of differential equations
  - Using neural ordinary differential equations as a memory-efficient RNN for
    deep learning
  - Automatic discovery of differential equations
  - Solving differential equations with neural networks

Homework 3: Solving 100 dimensional PDEs with deep learning

- Distributed parallel computing (Jeremy Kepner: Weeks 7-8)
  - Forms of parallelism
  - Using distributed computing vs multithreading
  - Message passing and deadlock
  - Map-Reduce as a framework for distributed parallelism
  - Implementing distributed parallel algorithms with MPI
- Probabilistic Programming, AKA Bayesian Estimation on Programs (Week 9)
  - The connection between optimization and Bayesian methods: Bayesian posteriors
    vs MAP optimization
  - Introduction to Markov-Chain Monte Carlo methods
  - Hamiltonian Monte Carlo is just a symplectic ODE solver
  - Uncertainty quantification of parameter estimates through posteriors
- Methods for understanding the fitness of models (Week 10)
  - Global sensitivity analysis
  - Fast methods for uncertainty quantification
  - Surrogate modeling techniques for accelerating sensitivity calculations
- Final Project Presentations (Weeks 11-12)

# Lecture Summaries and Handouts

Note that lectures are broken down by topic, not by day. Some lectures are more
than 1 class day, others are less.

## Lecture 0 (Optional): Introduction to Julia

Learn Julia Session, offered by Steven Johnson. Friday September 6, 5-7pm. Location: 32-141.
[Lecture Notes in Julia for Numerical Computation in MIT Courses](https://github.com/mitmath/julia-mit).

This is an optional session for learning to use Julia. It assumes no prior
programming experience.

## Lecture 1: Introduction to Scientific Machine Learning

#### Lecture Notes

- [What is Scientific Machine Learning?](https://mitmath.github.io/18337/lecture1/scientific_ml.pptx)

#### Optional pre-reading materials

- [The Essential Tools of Scientific Machine Learning](http://www.stochasticlifestyle.com/the-essential-tools-of-scientific-machine-learning-scientific-ml/)
- [Workshop videos on Scientific Machine Learning](https://icerm.brown.edu/events/ht19-1-sml/)

#### Summary

We will start off by setting the stage for the course. The field of scientific
machine learning and its span across computational science to applications in
climate modeling and areospace will be introduced. The methodologies that will be
studied, in their various names, will be introduced, and the general formula that
is arising in the discipline will be laid out: a mixture of scientific simulation
tools like differential equations with machine learning primitives like neural
networks, tied together through differentiable programming to achieve results
that were previously not possible.

## Lecture 2: Introduction to Code Optimization

##### Lecture Notes

- [Optimizing Serial Code](https://mitmath.github.io/18337/lecture1/optimizing)

##### Optional pre-reading materials

- [Optimizing Your DiffEq Code](http://tutorials.juliadiffeq.org/html/introduction/03-optimizing_diffeq_code.html)
- [Type-Dispatch Design: Post Object-Oriented Programming for Julia](http://www.stochasticlifestyle.com/type-dispatch-design-post-object-oriented-programming-julia/)

#### Summary

You will get nowhere in scientific machine learning with slow code. We need to
jam together partial differential equations and neural networks, and so we need
to know how to program both in an efficient manner. Here we will build a mental
model for the computer to understand how caches, heap allocations, function calls,
etc. make a program either fast or slow. We will also introduce the ideas of
type inference, multiple dispatch, and showcase how these features can be utilized
to generate fast code. JIT compilers don't make fast code: embedding knowledge
about the routine makes fast code.

## Lecture 3: Introduction to High Performance Computing Clusters (Supercloud)

### Guest Lecturer Lauren E Milechin

#### Note to students: [Get a supercloud account](https://supercloud.mit.edu/requesting-account)

- [MIT Supercloud Getting Started](https://supercloud.mit.edu/getting-started)
- [Supercloud Teaching Examples](https://github.com/llsc-supercloud/teaching-examples)

#### Summary

## Lecture 4: Introduction to Dynamical Systems

#### Optional pre-reading materials

- [Strogatz: Nonlinear Dynamics and Chaos](https://www.amazon.com/Nonlinear-Dynamics-Chaos-Applications-Nonlinearity/dp/0738204536)
- [Stability of discrete dynamics equilibrium](https://mathinsight.org/equilibria_discrete_dynamical_systems_stability)
- [Behavior of continuous linear dynamical systems](http://chrisrackauckas.com/assets/Papers/ChrisRackauckas-ContinuousDynamics.pdf)

Once the stage is set, we will start by developing the basics of our scientific
simulators: differential and difference equations. A quick overview of geometric
results in the study of differential and difference equations will set the stage
for understanding nonlinear dynamics, which we will quickly turn to numerical
methods to visualize. Here, the routines of numerical differential equations,
such as the Runge-Kutta and Adams-Bashforth methods, will shown as a way to
translate a continuous description of a system into a discrete one that is
amenable to computational simulation.

The discretization of a differential equation has some curious aspects which must
be appropriately handled in order to arrive at a suitably scalable scientific simulator.
This lecture will end by going into how serial scalar-heavy codes can be optimized.
SIMD, in-place operations, broadcasting, heap allocations, and static arrays will be
used to get fast codes for dynamical system simulation. These simulations will then
be used to reveal some intriguing properties of dynamical systems which will be
further explored through the rest of the course.

## Lecture 5: Ordinary Differential Equations Across the Sciences

## Lecture 6: Numerical Methods for ODEs

## Lecture 7: Within-Method and Data-Parallelism of ODE Solvers
