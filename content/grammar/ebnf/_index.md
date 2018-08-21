---
title: "EBNF"
date: 2018-08-20T23:47:43-03:00
weight: 16
---

For specifying the Claret grammar, we used the [Extended Backus-Naur Form (EBNF)](https://en.wikipedia.org/wiki/Extended_Backus–Naur_form), a family of metasyntax notation which is often used for formal description of programming languages.

{{< highlight ebnf "linenos=inline" >}}
sud ::= 'systemName' StrLiteral '{' usecase* '}'`
usecase ::= 'usecase' StrLiteral '{' versions? actor+ pre basic ( exception | alternative )* post '}'
versions ::= 'version' StrLiteral typeSpec user date
typeSpec ::= 'type' StrLiteral
user ::= 'user' StrLiteral
date ::= 'date' StrLiteral
actor ::= 'actor' ident StrLiteral
pre ::= 'preCondition' condition
post ::= 'postCondition' condition
steps ::= '{' ( action | response )+ '}'
action ::= 'step' numeric variable StrLiteral skipAlternative
response ::= 'step' numeric 'system' StrLiteral skipException
skipAlternative ::= af | as | bs
skipException ::= ef | as | bs
condition ::= StrLiteral ( ',' StrLiteral )*
basic ::= 'basic' steps
exception ::= 'exception' numeric StrLiteral steps
alternative ::= 'alternative' numeric StrLiteral steps
af ::= 'af' '[' numeric ( ',' numeric )* ']'
ef ::= 'ef' '[' numeric ( ',' numeric )* ']'
as ::= 'as' numeric ':' numeric
bs ::= 'bs' numeric
numeric ::= [0-9]+
variable ::= ident
{{< / highlight >}}
