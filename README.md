Explanation of Files
====================
Main.hs
-------
OVERVIEW: The top level, abstracted out file which contains the main method and will be compiled and run.
It essentially allows for the user to use one of the top level functions for RegEx matching, which are
1. Checking if matches exist (returnBool)
2. Returning all matches against the RegEx (returnMatches)
3. Returning only those matches that are within the extract constructor of the RegEx ('(' & ')') (returnExtractions)

Also runs all the unit tests.

DEPENDENCIES: Regex

Regex.hs
--------
OVERVIEW: This is the module which contains the structural information as well as the matching mechanisms for RegExes. It supports (), ^, $, ., *, +, ?, sequences and escaping. It also matches for boolean results, all possible matches and specific extractions.

This is the organizing module, which uses the parsing capabilities from Parser and ParserCombinators and RegEx matching from RegEx to first parse a string into a RegEx and then match that RegEx against a sample string to return the required result. We're using Monad Transformers to do the parsing.

In addition, it also includes Hughes Pretty Printer to print a given RegEx to its string equivalent.

Initially, we had it divided into two modules, one to manage the RegEx pattern matching, and one to do the parsing and pretty printing. However, there are certain rules about generating RegEx, which is why we wanted to ensure that RegExes are only generated from parsing a string, such that illegal RegExes can be caught as an error at parsing itself.

DEPENDENCIES: ParserTrans, ParserCombinators, Test.HUnit, Test.QuickCheck, Control.Monad, Text.PrettyPrint.HughesPJ

ParserTrans.hs
--------------

OVERVIEW: This is the Parser module which defines the required functions for parsing a RegEx from a string. It follows the structure developed in a previous homework assignment, using Monads and Monad Transformers.

DEPENDENCIES: Control.Monad.State

ParserCombinators.hs
--------------------

OVERVIEW: This is the Parser Combinators module developed in a previous homework which contains the various combinators which implement the Parser developed, such as between and choice. We're only using those that we need for our RegEx parser.

DEPENDENCIES: ParserTrans

External Libraries
==================
Hughes Pretty Printer for printing a RegEx as an equivalent string.
