# Optical Character Recognition of Complex Maths

This will be the evolution of a few experiments in converting complex math to LaTeX (and then by proxy to other formats like MathML, SVG, etc).  

- [Initial Attempt with Claud]([https://github.com/adligo/k3d-demo.py.adligo.org](https://github.com/adligo/k3d-demo.py.adligo.org/blob/main/src/math_ocr.py)
  
- [BitSlotMaps (aka BitVectors)](https://github.com/adligo/acp_solutions.py.adligo.com/blob/main/identification/IdentifyUpstreamOriginNodes/answerFinal.py)

# Next Steps

The basic plan is to filter the input image so that it becomes black and white pixels only.  Then turn each of these pixels into a 2d BitSlotMap (aka BitVector), which can be used to quickly identify the bounding boxes surrounding black pixels.  

## Bounding Box Strategy

### Left-Top, Right-Bottom

Identify the top left corner and bottom right corners of the bounding box of all of the content.  This and all other operations can be completed by comparing the BitSlotMaps for the columns or rows to zeros, since they are also integer numbers. 

### Sub Box Recursion

Recursively split up boxes using the following approach;

#####  Identify Vertical Splits

... Working through a meeting 

