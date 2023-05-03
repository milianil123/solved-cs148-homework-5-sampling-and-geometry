Download Link: https://assignmentchef.com/product/solved-cs148-homework-5-sampling-and-geometry
<br>
Introduction to Computer Graphics and Imaging

You’ll notice that this problem set is a few more pages than the usual CS 148 homework; part of this problem set is a reading assignment. The problems are intended to make sure you understand both what we’ve covered in class and what the narration below discusses: You are responsible for both on the final exam!

In the past few weeks, we have covered a diverse set of topics relevant to computer graphics, from sampling and Fourier theory to computer aided geometric design. In this homework, we will be exploring a number of these topics to help you get better acquainted with the issues we have discussed in class.

We’ll start by discussing some of the details of sampling theory laid out in class to help determine the resolution you need to display different continuous images. Recall that we stated the following “theorem” in class:

<strong>Theorem(-ish). </strong>Any <em>function can be written as a combination of simple wiggles.</em>

Of course, the word “any” here is very suspect, but as computer scientists we’ll ignore the intricacies of Lebesgue integration and Schwartz distributions in favor of an entirely un-rigorous approach.<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>

Before we define the Fourier transform, we should state a famous mathematical relationship that you likely have seen before:

<em>e<sup>iθ </sup></em>= cos <em>θ</em>+ <em>i </em>sin <em>θ                                                                                                                                                             </em>(1)

This equation often is called “Euler’s Formula.” Let’s fill in some details:

<ul>

 <li><em>e </em>= 718 . . . is the natural logarithm base.</li>

</ul>

√

<ul>

 <li><em>i </em>= −1 is the imaginary unit of the complex plane <strong>C</strong>.</li>

 <li><em>θ </em>∈ <strong>R </strong>is any real number.</li>

</ul>

If you never have seen (1), you should make the following straightforward observation: <em>This equation makes no sense</em>. And, you’re not wrong! In particular, raising any number to an imaginary exponent <em>i </em>isn’t a reasonable operation in the usual sense of exponentiation as “repeated multiplication.”

In fact, in many ways we can think of Euler’s formula as a <em>notational convenience</em>. We can prove that the right hand side of (1) behaves identically to exponentiation in almost every possible way. This observation allows us to compactify derivations of many facts we know from high school trigonometry. For instance, consider the following derivation:

cos(<em>θ</em>+<em>φ</em>)+ <em>i </em>sin(<em>θ</em>+<em>φ</em>) = <em>e<sup>i</sup></em><sup>(<em>θ</em></sup><sup>+<em>φ</em></sup><sup>) </sup>by (1)

= <em>e<sup>iθ</sup>e<sup>iφ </sup></em>by properties of exponentiation

= (cos <em>θ</em>+ <em>i </em>sin <em>θ</em>)(cos <em>φ</em>+ <em>i </em>sin <em>φ</em>) by (1)

= (cos <em>θ </em>cos <em>φ </em>− sin <em>θ </em>sin <em>φ</em>)+ <em>i</em>(sin <em>θ </em>cos <em>φ</em>+ cos <em>θ </em>sin <em>φ</em>) since <em>i</em><a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a> = −1

Make sure you understand each step here before moving on!

But, what did we just show? If you take the real and imaginary components of the left and right hand sides of the derivation above separately, we find:

cos(<em>θ</em>+<em>φ</em>) = cos <em>θ </em>cos <em>φ </em>− sin <em>θ </em>sin <em>φ </em>sin(<em>θ</em>+<em>φ</em>) = sin <em>θ </em>cos <em>φ</em>+ cos <em>θ </em>sin <em>φ</em>

You probably worked much harder to prove these statements in high school trigonometry.

Anyway, our goal today is to understand the Fourier transform of a function. We now have all the tools we need to do so.

<strong>Definition </strong>(Fourier Transform)<strong>. </strong><em>The Fourier transform of a function f </em>: <strong>R </strong>→ <strong>R </strong><em>is the function f</em>ˆ(<em><sub>ξ</sub></em>) <em>given by</em>

<em>f</em>ˆ<em> dx                                                                                                                                      </em>(2)

The variable <em>ξ </em>here represents a frequency. So, <em>f</em>ˆ(<em>ξ</em>) represents the “component” of <em>f </em>that wiggles at frequency <em>ξ</em>.

<strong>Problem 1 </strong>(10 points)<strong>. </strong><em>Recall that in Lecture 11 of CS 148 we stated that the Fourier transform does the</em>

<em>“simplest possible thing:” multiplying a function against a wiggle at a fixed frequency and integrating. Use Euler’s formula </em>(1) <em>to justify why the Fourier transform </em>(2) <em>does exactly this. Why does f</em>ˆ(<em><sub>ξ</sub></em>) <em>need real and imaginary components?</em>

As tempting as it is for your mathematician instructor, we will not derive most of the (beautiful) relationships between properties of a function and properties of its Fourier transform. There is, however, one relationship that is fundamental to the sampling theory we discussed in lecture.

<strong>Problem 2 </strong>(15 points)<strong>. </strong><em>Take any real number a </em><em>&gt; </em>0<em>, and define h</em>(<em>x</em>) = <em>f</em>(<em>ax</em>)<em>. Derive the following relationship:</em>

<em>h</em>ˆ                                                                                                                                                           (3)

<em>Explain how this relationship substantiates the claim made in class that increasing the rate at which you sample a (band-limited) function makes it less likely that you will see artifacts.</em><sup>2</sup>

Figure 1: For problem 3(a).

<strong><em>Hint: </em></strong><em>To derive </em>(3)<em>, substitute h into the definition of the Fourier transform and make the substitution y </em>= <em>ax.</em>

There are myriad other facts we could derive from the Fourier transform <em>f</em>ˆ that are relevant to sampling theory as it applies to computer graphics, but we’ll abandon our discussion at this point in favor of moving to the topic of geometric modeling.

<strong>Problem 3 </strong>(10 points)<strong>. </strong><em>(a) The control points of a quadratic Be´zier curve g</em>(<em>t</em>) <em>and a cubic Be´zier curve f</em>(<em>t</em>) <em>are shown in Figure 1. Construct the points g</em>(3/2) <em>and f</em>(1/3)<em>. You’ll need to turn in a copy of Figure 1 with your constructions drawn on top; you may wish to enlarge these structures and/or print them on separate pages for more space. (b) Find the (quadratic and cubic, resp.) blossoms of the functions g</em>(<em>t</em>) = <em>t</em><sup>2 </sup>− 2<em>t </em>+ 1 <em>and h</em>(<em>t</em>) = (<em>t </em>− 2)<sup>3</sup><em>.</em>

One of the key ideas of computer-aided geometric design (CAGD) as it pertains to curves is that of finding a <em>basis </em>for polynomial functions of a given degree. As we discussed in lecture, the idea of a basis here is slightly more abstract than what you might have seen in Math 51, so it’s worth putting some thought into our construction.

We consider a basis of the set of polynomials of degree <em>n </em>to be a set of <em>n </em>+ 1 polynomial functions <em>p</em><sub>1</sub>(<em>t</em>), . . . , <em>p<sub>n</sub></em><sub>+1</sub>(<em>t</em>) such that <em>any </em>degree-<em>n </em>polynomial can be written as a linear combination of these <em>p<sub>i</sub></em>’s. For example, an obvious basis for the degree-three polynomials would be <em>p</em><sub>1</sub>(<em>t</em>) = 1, <em>p</em><sub>2</sub>(<em>t</em>) = <em>t</em>, <em>p</em><sub>3</sub>(<em>t</em>) = <em>t</em><sup>2</sup>, <em>p</em><sub>4</sub>(<em>t</em>) = <em>t</em><sup>3</sup>. Why? Because the general form of a degree-three

polynomial is <em>at</em><sup>3 </sup>+ <em>bt</em><sup>2 </sup>+ <em>ct </em>+ <em>d</em>, or equivalently <em>ap</em><sub>4</sub>(<em>t</em>)+ <em>bp</em><sub>3</sub>(<em>t</em>)+ <em>cp</em><sub>2</sub>(<em>t</em>)+ <em>dp</em><sub>1</sub>(<em>t</em>).

Certain polynomial bases are convenient for certain problems, so a strategy in CAGD is to work in a basis that simplifies our math as much as possible. We explored this strategy in class when we derived the Hermite basis, which simplified the problem of finding a curve with given begin and end points/tangents. In our final written problem, we will derive an alternative basis for cubic polynomials simplifying math for Bezier curves.´

<strong>Problem 4 </strong>(15 points)<strong>. </strong><em>Suppose we label the control points</em><em>~a,</em><em><sup>~</sup>b,</em><em>~c, and d of a cubic curve in Figure 2 and</em><em><sup>~ </sup>use the structure drawn to find the point f</em>(<em>t</em>) <em>(assume the control points specify the curve between f</em>(0) <em>and f</em>(1)<em>). Label the constructed points as linear combinations of the control points; we provide you with one label to get you started. Use your label for f</em>(<em>t</em>) <em>to define the Bernstein basis for cubic polynomials, that is, a basis that makes it easy to write down the cubic curve associated with a set of four control points.</em>

Figure 2: For problem 4.

Figure 3: Examples of MLS output.

For the coding part of this assignment, you will implement the <em>Moving Least Squares </em>(MLS) image deformation algorithm introduced in SIGGRAPH 2006.<a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a> Examples of the output of MLS are shown in Figure 3. The purpose of this algorithm is fairly straightforward: The user marks a number of “handles” on an image and then starts moving them around. As the handles are moved, the image deforms smoothly while satisfying the constraints that the handles are mapped to their targets. MLS can be used to achieve lots of interesting image effects with relatively simple computations.

To motivate MLS, we first consider a slightly easier problem. Let’s say we mark a number of points <em>~p</em><sub>1</sub>, . . . ,<em>~p<sub>n </sub></em>∈ <strong>R</strong><sup>2 </sup>on the plane, and we specify a list of targets <em>~q</em><sub>1</sub>, . . . ,<em>~q<sub>n </sub></em>∈ <strong>R</strong><sup>2</sup>. We wish to find an <em>affine </em>transformation of the plane given by <em>~p</em>for some <em>M </em>∈ <strong>R</strong><sup>2</sup><sup>×2</sup>,<em><sup>~</sup>t </em>∈ <strong>R</strong><sup>2 </sup>such that <em>M</em> for each <em>i </em>∈ {1, . . . , <em>n</em>}. When is <em>n </em><em>&gt; </em>2, the ≈ is key: it might be the case that <em>no </em>affine transformation can map all the <em>~p<sub>i</sub></em>’s to their corresponding<em>~q<sub>i</sub></em>’s exactly!

Thus, we can only hope to approximate such a relationship. To this end, we’ll introduce one more set of inputs: a set of “weight” values <em>w</em><sub>1</sub>, . . . , <em>w<sub>n </sub></em><em>&gt; </em>0. A large weight <em>w<sub>i </sub></em>says we really care that <em>~p<sub>i </sub></em>maps to , while a small <em>w<sub>i </sub></em> 1 means we don’t really care if <em>M </em>and<em><sup>~</sup>t </em>don’t do a good job mapping <em>p<sub>i </sub></em>to <em>q<sub>i</sub></em>.

Note that if <em>M</em><em>                           </em><em><sup>~                                                                            </sup></em>then <em>M</em><em>           </em>0. In other words, we desire that

<em>~q<sub>i</sub></em>k<sup>2 </sup>≈ 0. So, let’s define an energy:

<em>n</em>

<em>E</em>(<em>M</em>,                                                                                                                               (4)

<em>i</em>=1

We can make a number of important observations about <em>E</em>:

<ul>

 <li>We always have <em>E </em>≥</li>

 <li>If there exist<em><sup>~</sup>t </em>and <em>M </em>such that <em>~q<sub>i </sub></em>= <em>M</em>exactly for <em>all i </em>∈ {1, . . . , <em>n</em>}, then <em>E </em>will be minimized with value 0 at this point.</li>

 <li>When such a zero minimum is not possible, the minimum <em>E </em><em>&gt; </em>0 occurs when <em>M </em>and <em><sup>~</sup>t </em>give the best affine map approximating <em>~p<sub>i </sub></em>7→ <em>~</em><em>q<sub>i </sub></em>in a “least squares” sense. The weights <em>w<sub>i </sub></em>prioritize with ) pairs matter the most.</li>

</ul>

Thus, if the user inputs lots of pairs ), we can frame an optimization problem to find <em>M </em>and

<em>~t </em>as follows:

min        <em>E</em>(<em>M</em>,<em>~t</em>)                                                                                                                                                           (5)

<em>M</em>∈<strong>R</strong>2×2,<em>~</em><em>t</em>∈<strong>R</strong>2

You probably spent much of calculus class solving problems exactly of this nature! Simply take derivatives of <em>E </em>with respect to the elements of <em>M </em>and<em><sup>~</sup>t</em>, set them to zero, and solve.

We’ll resist the urge to force you to derive these formulas yourself, although you’re encouraged to check them on scratch paper; our discussion above plus a few tricks from Math 51 are all you need. Instead, we’ll jump right to the solution of our minimization problem (5). To clean up our notation a bit, let’s define some helper variables:

<em>w</em><em>i</em><em>~p</em><em>i</em>

(6) <em>w<sub>i</sub></em>

<em>w</em><em>i</em><em>~q</em><em>i</em>

(7) <em>w<sub>i</sub></em>

It’s easy to differentiate (5) with respect to the elements of<em><sup>~</sup>t </em>(at least try this part at home!), yielding the following relationship when we set this derivative to zero:

<em>~t</em><em>opt </em>=<em>~</em><em>q</em>∗ − <em>M</em><em>opt</em><em>~p</em>∗                                                                                                                                                                                                                                         (8)

That is, we can find the optimal translation<em><sup>~</sup>t<sub>opt </sub></em>easily enough once we know the optimal matrix

<em>M</em><em>opt</em>.

Finding <em>M<sub>opt </sub></em>takes a bit more bookkeeping. We’ll need two more sets of helper variables:

<em>p</em>ˆ<em><sub>i </sub></em><sup>∗              </sup>(9) <em>q</em>ˆ<em><sub>i </sub></em>=<em>~</em><em>q<sub>i </sub></em>−<em>~</em><em>q</em><sup>∗ </sup>(10) We can reduce finding <em>M<sub>opt </sub></em>to a least-squares problem, so when the smoke clears we’ll get the following “normal equation” solution:

!−1

<em>M</em><em>optw</em><em>jq</em>ˆ<em>jp</em>ˆ<em>w</em><em>ip</em>ˆ<em>ip</em>ˆ<em>i</em>&gt;                                                                                                                                                                                                            (11)

This finishes our story. From the inputs , . . . , (<em>~</em><em>p<sub>n</sub></em>,<em>~q<sub>n</sub></em>, <em>w<sub>n</sub></em>) we can compute <em>~p</em><sup>∗ </sup>and <em>~q</em><sup>∗</sup>. We can use these to compute <em>p</em>ˆ<em><sub>i </sub></em>and <em>q</em>ˆ<em><sub>i </sub></em>for all <em>i</em>. Then, we use (11) to compute <em>M<sub>opt</sub></em>. Finally, we find<em><sup>~</sup>t<sub>opt </sub></em>using (8). The formulas might look complicated, but they’re quite simple to evaluate; the 2 × 2 inverse in (11) can be found in closed-form with the usual formula (built into Eigen using the .inverse() method of Matrix2d).

We may wish to put additional constraints on <em>M<sub>opt</sub></em>. It’s easy to see that regardless of our constraints on <em>M<sub>opt</sub></em>, the formula (8) for<em><sup>~</sup>t<sub>opt </sub></em>stays the same. This aside, if we want only to consider <em>similarity </em>matrices <em>M </em>that contain no shear–that is, they only can rotate and scale–then we constrain <em>M</em><sup>&gt;</sup><em>M </em>= <em><sub>λ</sub></em><sup>2</sup><em>I </em>for some <em><sub>λ </sub></em>∈ <strong>R </strong>(think about why!) and find:

<em>similarity         </em>1   <em>n</em>

<em><sup>M</sup></em><em><sub>opt              </sub></em>= ∑ <em>w<sub>i                                                        </sub>p</em>ˆ<em><sub>i                i                                                                                                                                                   </sub></em>(12)

<em><sup>µ </sup></em><em>i</em>=1                      <em>i</em>

where

<em>n</em>

<em>µ </em>= ∑ <em>w<sub>i</sub></em>k<em>p</em>ˆ<em><sub>i</sub></em>k<sup>2                                                                                                                                                                                                                                                  </sup>(13)

<em>i</em>=1

If we force <em>M </em>only to encode rotations without any scaling, then (12) still works, but we replace <em>µ </em>with

<em>µ</em>˜                                                                                               (14)

Here, for vector<em>~a </em>= (<em>a</em><sub>1</sub>, <em>a</em><sub>2</sub>) we denote<em>~a</em><sup>⊥ </sup>= (−<em>a</em><sub>2</sub>, <em>a</em><sub>1</sub>).

MLS simply applies the formulas we developed above with a clever choice of the <em>w<sub>i </sub></em>values. We’re going to render an image by drawing a <em>k </em>× <em>k </em>grid of quads with evenly-spaced texture coordinates. In our code the grid of texture coordinates is stored in the variable textureCoords; you should <em>not </em>change the values in this array. We’ll deform the grid to a new set of positions (stored in imageCoords) using the MLS algorithm and render the deformed image using textured triangles; see display() to see our basic setup.

The user shift-clicks the control points <em>~p<sub>i </sub></em>to make red handles appear (shift-clicking those red handles again makes them disappear); the indices of these points in imageCoords are stored in the set active. The user then can drag the handles to new targets<em>~q<sub>i</sub></em>, the positions of which are stored in imageCoords. This much functionality is implemented for you in the skeleton code.

Your job is to implement deformImage(), which writes new values for elements of the array imageCoords. The basic algorithm goes like this:

<ul>

 <li>Iterate over each texture coordinate <em>~p </em>in the array textureCoords.</li>

 <li>If <em>~p </em>is one of the <em>~p<sub>i</sub></em>’s, then its position in imageCoords is <em>~q<sub>i </sub></em>and can be left alone. Otherwise proceed with the steps below.</li>

 <li>Compute weights <em>w<sub>i </sub></em>for the provided constant <em>α </em><em>&gt; </em> Recall that <em>~p<sub>i </sub></em>denotes the texture coordinate of the <em>i</em>th point in active. Notice what this choice of <em>w<sub>i </sub></em>is doing: Control points that are close to <em>~p </em>get more weight than those that are far away.</li>

 <li>Compute <em>M<sub>opt </sub></em>and<em><sup>~</sup>t<sub>opt </sub></em>using the weights <em>w<sub>i </sub></em>you just computed and the formulas above.</li>

 <li>Replace the position in imageCoords with<em>~q </em>= <em>M<sub>opt</sub></em><em>~p </em>.</li>

</ul>

In other words, each (sampled) point on the base texture computes its own least-squares map and uses that map to find a target.

<strong>Problem 5 </strong>(50 points)<strong>. </strong><em>Implement MLS deformation starting from the skeleton code. You must implement the affine, similarity, and rotation-only versions of the algorithm, using command line options stored in deformationType to determine what to do in the application.</em>

<strong>Problem 6 </strong>(5 points extra credit)<strong>. </strong><em>When does our choice of w<sub>i </sub>in MLS break down? Can you suggest a replacement? Describe your solution in the written homework; no need to add it to your code, as the implementation change might (hint!) require a using a structure other than a grid mesh–a considerable change!</em>

<a href="#_ftnref1" name="_ftn1">[1]</a> Please come to Justin’s office hours or post on Piazza if you would like work out the details of making this theory more rigorous. Some fascinating and deep mathematics are hiding in the straightforward-looking derivations we cover in CS 148!

<a href="#_ftnref2" name="_ftn2">[2]</a> For students with a strong math background, note that in CS 148 you need not be concerned with whether your integrals converge or are well-defined: feel free to apply and reasonable-looking operation without regard for such analytical details!

<a href="#_ftnref3" name="_ftn3">[3]</a> You’re encouraged to read the original paper for a more detailed discussion. Note that the paper uses row rather than column vectors, so their math is a bit different.