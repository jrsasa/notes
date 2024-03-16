[[矩阵设计]]
 Constraining the measurement matrix in this manner raises the following fundamental question: 
 **How do we best choose the index set Ω?** 
 The answer depends on the structure known to be inherent in x, as well as the recovery algorithm used.

Idea:
We select the indices that preserve as much energy as possible in a set of training signals, either in a worst-case or average case sense, and we show that this is also equivalent to minimizing the l2-error achieved by a simple linear decoder.

By identifying combinatorial optimization structures we show that we can find exact or near-exact solutions to these optimization problems

provide both deterministic and statistical theoretical guarantees characterizing how well the selected set of indices perform when applied to new signals differing from the training set

demonstrate the effectiveness of our approach on a variety of data sets, showing matching or improved performance

Decoders:linear decoding and basis pursuit decoding
Related work:
Variable-density Subsampling
:considered randomized choices of $\Omega$ and sought the corresponding distributions,rather than fixed choices.
Learning-based Measurement Designs