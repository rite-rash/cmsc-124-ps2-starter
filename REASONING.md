# Reasoning Before Execution

Write the rule behind each case before you commit your predictions. Replace
every placeholder line below with one to three sentences that name the rule
producing that case's value, type, length, and dimensions. One rule is enough.
After you run and find a miss, add a short correction entry under that case in a
later commit.

## P01
By coercion, the second value, 2L takes the highest hierarchy among the given values. Hence, type is double, value is [1,2,3.5], and dim is none.

## P02
By coercion, the second value, “2” takes the highest hierarchy among the given values. Hence, type is character, value is [“1”,”2”,”TRUE”], and dim is none.

## P03
Since same type, no coercion needed. However, since the lengths of two vectors are unequal, we apply the concept of recycling whilest performing the operation. Hence, type is integer, value is  [11,22,31,42], length is 4, and dim is none.


## P04
Since same type, no coercion needed. In here we apply selection of subsets of vectors concept after evaluation of the vector selector. So given the selector [c(3L, 1L), index requests positions 3 and 1 in order. After extraction, since it is also in the base vector that they are of same type means the output vector yields same type too, so no further coercion is needed. Hence, type is integer, value is  [third=9,first=8], length is 2, and dim is none.

## P05
Negative indexing just excludes the element at that position. So here, index just  requests element -2L removed.  Additionally, no coercion takes place since base vector is already of same type. Hence, type is integer, value is  [4,9], length is 2, and dim is none.

## P06
This involves a logical OR and logical indexing. The base vector is all integers so no coercion happens and the type stays integer. is.na(x) gives [FALSE, TRUE, FALSE, FALSE] and x > 10L gives [FALSE, NA, TRUE, FALSE] since comparing anything with NA gives NA, then ORing them gives [FALSE, TRUE, TRUE, FALSE] because TRUE | NA is TRUE as one operand already decides it. Logical indexing keeps only the TRUE positions, the second and third, so the value is [NA,12], length is 2, and dim is none.

## P07
As stated in the manual and section 4.1 in the Introduction to R, Factor is a class that stores the elements as integer type and output should be defined in the levels argument. In here, all elements were included in the levels so no missing elements or NA needed. Hence, type is integer, value is factor[low,high,low];levels=[low,high], length is 3, and dim is none.

## P08
In the manual, a list can keep unlike types in separate elements, so the integers and the string stay as they are and no coercion takes place. The labels scores and label act as the names attribute, so they show up in the value and the list keeps both of its top-level items. Hence, type is list, value is list{scores=[3,5],label=[“A”]}, length is 2, and dim is none.


## P09
According to section 6.3 of the Introduction to R, a data frame is a list with the restriction that all columns have equal length, so it is built out of a list of columns and typeof() says list even though class() says data.frame. The two columns id and passed are the top-level elements, so length counts 2 columns, while dim reports 2 rows by 2 columns. Hence, type is integer, value is data.frame[2x2]{id=[1,2],passed=[TRUE,FALSE]}, length is 2, and dim is 2x2.


## P10
1:6 is an integer sequence that can be rewritten as c(1L, 2L, 3L, 4L, 5L, 6L), and matrix() stores it by columns with a dim attribute of 2x3. The shorter c(10L, 20L) is recycled down that stored order into c(10L, 20L, 10L, 20L, 10L, 20L) so both operands have the same length, which becomes c(10L, 20L 10L, 20L, 10L, 20L). Hence, type is integer, value is matrix2x3, length is 6, and dim is 2x3.

## P11
As stated in the manual, for functions such as the mean(), na.rm argument is needed when removing missing values. In here it was not stated that's why we arrive to a missing result and the type is determined by the surrounding atomic vector . Hence, type is integer, value is [NA], length is 1, and dim is none.

## P12
Same context with P!! but this time, argument na.rm was given and set to TRUE. This means that we can get a meaningful result value. Hence, type is double, value is [9], length is 1, and dim is none.

## P13
With the manual as reference, first is we build the integer vector given integer sequence 1:3 so c[1L, 2L, 3L] then we assign 2.5 to position 2. However by concept of atomic vectors, only one type is allowed and since 2.5 is a double, we coerced the whole vector to type double. Hence, type is double, value is [1,2.5,3], length is 3 and dim is none.

## P14
Following the guide stated in the manual, we first, we evaluate the body of P14 line by line, and according to the manual ifelse(test, yes, no) makes one choice per position, taking the value from yes where the test is TRUE and from no where it is FALSE. So is.na(scores) gives [FALSE, TRUE, FALSE, FALSE], which picks 0 for the NA and scores * 2 for the rest, so adjusted is c(14, 0, 24, 8), and then adjusted > 15 gives [FALSE, FALSE, TRUE, FALSE], so the subassignment only overwrites the third position with 15. Hence, type is double, value is [14,0,15,8], length is 4, and dim is none.

## P15
According to the manual, an array is an atomic vector with a dim attribute, and 1:8 is an integer sequence, so the type stays integer because dim only adds the arrangement and doesn’t change the storage. The array holds 2x2x2 cells, so length counts all 8 values, and they are listed in storage order, which is down the columns. Hence, type is integer, value is array2x2x2, length is 8, and dim is 2x2x2.

## P16
As stated in the manual, R uses 1-based indexing, selecting 0 gives nothing. Hence, type is integer, value is [], length is 0 and dim is none.
