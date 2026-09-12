# Multiset Ternary ScaleTransform & F3 Field Verification

```idris
module Wiki.TernaryScaleTransformSpec

import Core.BoxInt
import Core.ScaleTransform
import Core.NarayAlphabet
import Logic.TernaryLogic
import Wiki.Generators
import public QuickCheck

%default total
```

## QuickCheck Verification Properties

```idris
public export
prop_bit3ScaleTransformBounded : Bit3 -> Bool
prop_bit3ScaleTransformBounded b =
  let i : Integer = scaleTransform b
  in i >= -1 && i <= 1

public export
prop_bit3InvertScaleGalois : Bit3 -> Bool
prop_bit3InvertScaleGalois b =
  let i : Integer = scaleTransform b
      b' : Bit3 = invertScaleTransform i
  in b' == b

public export
prop_bit3Involution : Bit3 -> Bool
prop_bit3Involution b =
  notBit3 (notBit3 b) == b

public export
prop_bit3AdditiveInverse : Bit3 -> Bool
prop_bit3AdditiveInverse b =
  addBit3 b (notBit3 b) == Bit3Zero

public export
auditTernaryScaleTransformSpecProof : IO Bool
auditTernaryScaleTransformSpecProof = do
  let r1 = qc prop_bit3ScaleTransformBounded
  let r2 = qc prop_bit3InvertScaleGalois
  let r3 = qc prop_bit3Involution
  let r4 = qc prop_bit3AdditiveInverse
  pure (r1.pass == Just True && r2.pass == Just True && r3.pass == Just True && r4.pass == Just True)
```
