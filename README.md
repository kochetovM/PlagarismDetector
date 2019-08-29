# PlagarismDetector
Description

The algo performs plagiarism detection using a N-tuple comparison algorithm allowing for synonyms in the text.

The program takes in 3 required arguments, and one optional. In other cases such as no arguments, the program prints out usage instructions. 

1) file name for a list of synonyms
2) input file 1
3) input file 2
4) the number N, the tuple size. (by default is N=3)

The synonym file has lines each containing one group of synonyms. For example a line saying "run sprint jog" means these words should be treated as equal.

The input file1 should be declared plagiarized based on the number of N-tuples in file1 that appear in file2 (in other words we are looking for tuples in file1 that matches a source (file2) against which we are checking the percentage of plagarism in file1), where the tuples are compared by accounting for synonyms as described above. For example, the text "go for a run" (file1) has two 3-tuples, ["go for a", "for a run"] both of which appear in the text "go for a jog" (file2).

The output of the program is the percent of tuples in file1 which appear in file2. So for the above example, the output would be one line saying "100%". In another example, for texts "go for a run" and "went for a jog" and N=3 we would output "50%" because only one tuple in the first text appears in the second one.




# Algorithm

The Algorithm is broken into following main steps

	1.	Synonym File is broken into HashMap such that each word using as key and point to the set of his synonyms as value.
  
			D[run]: {fog, sprint, jog}

	2.	First file is parsed by words and broken to a list.

	3.	Second File file is parsed and all tuples are constructed and added to HashMap.

We will brake File_2 to N-sized hashmap of tuples where each word of the tuple is linked to next one by key-value: 
	
  Dict[word_1]: d2:[word_2] : ... d_n[word_N]: None
  
  It will give us instant search time to find a certain word of a tuple


4.  Search function. Where we are looking for a tuple from first file in the second by each word  in the tuple. We do it in this way instead of checking whole tuple as a key in hash-map because  we have to check also if each word has a synonyms. 
We actually also could do it by checking whole tuple as a key in hash-map, and in this way we would need to add to hashamp each set of word replaced by his synonyms. It would give us more complexity in first step of converting data structure but it will be better complexity when we do the search and compare. 


