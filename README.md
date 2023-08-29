# Poly_Module-3
Polygon is asking you to design a new zkSNARK circuit that implements some logical operations. You need to implement the circuit and deploy a verifier on-chain to verify proofs generated from this circuit

**Description**

Poly Advance Module 3: This module helps in studying about Zero-knowledge proofs and in this project we implement the working of a circuit provided in the assignment using logic gates implementation. The code walkthrough and working of the project has been explained in this Loom video.

**code**
pragma circom 2.0.0;

/*This circuit template checks that c is the multiplication of a and b.*/  

template Multiplier2 () {  

   //input signals
   signal input a;
   signal input b;

   //Gate signals
   signal X;
   signal Y;

   //Output signals
   signal output Q;

   //Component gates
   component andGate = AND();
   component notGate = NOT();
   component orGate = OR();

   //Logic of circuits
   andGate.a <== a;
   andGate.b <== b;
   X <== andGate.out;

   notGate.in <== b;
   Y <== notGate.out;

   orGate.a <== X;
   orGate.b <== Y;
   Q <== orGate.out;

}

template OR(){
   signal input a;
   signal input b;
   signal output out;
   out <== a+b-a*b;
}

template NOT(){
   signal input in;
   signal output out;
   out <== 1+in-2*in;
}

template AND(){
   signal input a;
   signal input b;
   signal output out;
   out <== a*b;
}

component main = Multiplier2();

**Authors**

Vishnu Vishvas Sharma
