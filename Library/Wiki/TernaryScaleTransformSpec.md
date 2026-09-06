# Multiset Ternary ScaleTransform & F3 Field Verification

```idris
module Wiki.TernaryScaleTransformSpec

import Core.BoxInt
import Core.ScaleTransform
import Core.NarayAlphabet
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
auditTernaryScaleTransformSpecProof : IO Bool
auditTernaryScaleTransformSpecProof = do
  let r1 = qc prop_bit3ScaleTransformBounded
  let r2 = qc prop_bit3InvertScaleGalois
  pure (r1.pass == Just True && r2.pass == Just True)
```
