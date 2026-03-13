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

#####  Identify Vertical Segments

Move from left to right and identify any columns that do not contain any blank pixels (1's).  This should be extremely fast since each column is a BitSlotMap (aka BitVector, integer number).  

#####  Identify Horizontal Segments

Move from top to bottom and identify any rows that do not contain any blank pixels (1's).  This should be extremely fast since each row is also a BitSlotMap (aka BitVector, integer number).  

#####  Identify Subtracted boxes

Move from top left to bottom right in a diagonal fashion, looking for boxes in all four directions.  Any subtractable Box is a hit and should be noted.  Exit after a single subtractable box is found.  Then move down one pixel and continue, and then to the right of the center and continue. Iterate until all pixels have been checked for subtractable boxes. 

## Store Bounding Boxes in JSON

Store all the bounding boxes in a JSON structure. 

## Single character identification. 

Concurrently, take all of the bounding boxes and identify a single character using AI.  The output of this should be LaTeX. 

## Final equation submission. 

Take the original content box's BitSlotMap, in the JSON with the LaTeX included, and submit it as a document to the final machine learning algorithm.
