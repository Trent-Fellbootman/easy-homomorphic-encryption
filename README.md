# A Method for Homomorphic Encryption Supporting Add, Subtract, Multiply and Deep Neural Networks

## How to do homomorphic encryption

An easy way to do homomorphic encryption on floating point numbers is:

1. Represent the number you want to encrypt in the following form:
   
   $x = a_1 k_1 + a_2 k_2 + \dots + a_n k_n$

   The vector $\mathbf{k} = (k_1, \dots, k_n)^T$ is your encryption key; the vector $\mathbf{a} = (a_1, \dots, a_n)^T$ is your cipher text.

2. Send the cipher text and do math operations (add / subtract / multiply) on it.

3. Retrieve the result of the previous step and decode.

## Why does it work?

Take multiplication as an example.

Assume we have a key $\mathbf{k} = (k_1, \dots, k_n)^T$ and two pieces of cipher text (cipher number),
$\mathbf{a} = (a_1, \dots, a_n)^T$ and $\mathbf{b} = (b_1, \dots, b_n)^T$.
The corresponding unencrypted numbers are $x = a_1 k_1 + a_2 k_2 + \dots + a_n k_n = \mathbf{a}^T\mathbf{k}$,
and $y = \mathbf{b}^T\mathbf{k}$.

The result of the multiplication is $xy = \mathbf{k}^T(\mathbf{a}\mathbf{b}^T)\mathbf{k}$.
We can apply multiplication on the cipher text and obtain $C = \mathbf{a}\mathbf{b}^T$,
and decode the result into $xy = \mathbf{k}^TC\mathbf{k}$.

Add & subtract works similarly.

Essentially, instead of using binary or decimal forms,
we are turning the base for representing the number into the key, $\mathbf{k}$.

## How useful is it?

Now that we can apply add and multiply on cipher text, we can basically apply any function $f$ on cipher text;
just use the Taylor Expansion of $f$.

Particularly, we can use it in deep neural networks (inference) and process sensitive data on the cloud.

## Future Work

I just got this idea a few days ago, haven't really dug into it or performed security or complexity analysis,
cuz I'm too busy with my schoolwork.
I might do some further research into this method and probably write a paper about it when I have time.
