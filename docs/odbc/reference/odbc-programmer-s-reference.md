---
title: Référence du programmeur de l’ODBC&#39;(fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], reference
ms.assetid: b33c3c43-ae66-44a3-be17-9cd82624dd96
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a9ca32627b9703465dcfca554fdc32ae01442e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280509"
---
# <a name="odbc-programmer39s-reference"></a>Référence du programmeur de l’ODBC&#39;
La *référence du programmeur ODBC* contient les sections suivantes.  
  
-   [Quoi de neuf dans ODBC 3.8](../../odbc/reference/what-s-new-in-odbc-3-8.md) répertorie les nouvelles fonctionnalités ODBC qui ont été ajoutées dans windows 8 SDK.  
  
-   [Le programme de l’échantillon ODBC](../../odbc/reference/sample-odbc-program.md) présente un exemple de programme ODBC.  
  
-   [Introduction à ODBC](../../odbc/reference/introduction-to-odbc.md) fournit une brève histoire de la langue de requête structurée et ODBC, et des informations conceptuelles sur l’interface ODBC.  
  
-   [Le développement d’applications](../../odbc/reference/develop-app/developing-applications.md) contient des informations sur le développement d’applications qui utilisent l’interface ODBC et les pilotes qui l’implémentent.  
  
-   [L’installation et la configuration du logiciel ODBC](../../odbc/reference/install/installing-and-configuring-the-odbc-software.md) fournissent des informations sur l’installation et une référence de fonction DLL de configuration.  
  
-   [Le développement d’un pilote ODBC](../../odbc/reference/develop-driver/developing-an-odbc-driver.md) contient des informations sur l’écriture d’un conducteur.  
  
-   [API Reference](../../odbc/reference/syntax/odbc-reference.md) contient des informations syntaxiques et sémantiques pour toutes les fonctions ODBC.  
  
-   [Les annexes ODBC](../../odbc/reference/appendixes/odbc-appendixes.md) contiennent des détails techniques et des tableaux de référence pour les codes d’erreur, les types de données et la grammaire SQL d’ODBC.  
  
## <a name="working-with-the-odbc-documentation"></a>Travailler avec la documentation de l’ODBC  
 L’interface ODBC est conçue pour une utilisation avec le langage de programmation C. L’utilisation de l’interface ODBC s’étend sur trois domaines : les instructions SQL, les appels de fonctions ODBC et la programmation en C. Cette documentation suppose ce qui suit :  
  
-   Une connaissance pratique du langage de programmation C.  
  
-   Connaissances générales DBMS et familiarité avec SQL.  
  
 Les conventions typographiques suivantes sont utilisées.  
  
|Format|Utilisé pour|  
|------------|--------------|  
|SÉLECTIONNEZ À PARTIR DE|Les lettres De Uppercase indiquent les déclarations SQL, les noms macro et les termes utilisés au niveau de commande du système d’exploitation.|  
|`RETCODE SQLFetch(hdbc)`|La police monospace est utilisée pour les lignes de commande d’échantillons et le code du programme.|  
|*Argument*|Les mots italicisés indiquent des arguments programmatiques, des informations que l’utilisateur ou l’application doit fournir, ou l’accent sur les mots.|  
|**SQLEndTran**|Le type audacieux indique que la syntaxe doit être tapée exactement comme indiqué, y compris les noms de fonction.|  
|&#124;|Une barre verticale sépare deux choix mutuellement exclusifs dans une ligne de syntaxe.|  
|...|Une ellipsis indique que les arguments peuvent être répétés plusieurs fois.|  
|. . .|Une colonne de trois points indique la continuation des lignes de code précédentes.|  
  
## <a name="about-the-code-examples"></a>À propos des exemples de code  
 Les exemples de code de ce guide sont conçus uniquement à des fins d’illustration. Parce qu’ils sont écrits principalement pour démontrer les principes de l’ODBC, l’efficacité a parfois été mise de côté dans l’intérêt de la clarté. En outre, des sections entières de code ont parfois été omises pour plus de clarté. Il s’agit notamment des définitions des fonctions non-ODBC (ces fonctions dont les noms ne commencent pas par "SQL") et la plupart des manipulations d’erreurs.  
  
 Tous les exemples de code utilisent les chaînes ANSI et le même schéma de base de données, qui est montré au début des [fonctions de catalogue](../../odbc/reference/develop-app/catalog-functions.md).  
  
## <a name="recommended-reading"></a>Lecture recommandée  
 Pour plus d’informations sur SQL, les normes suivantes sont disponibles :  
  
-   Langage de base de données - SQL avec amélioration de l’intégrité, ANSI, 1989 ANSI X3.135-1989.  
  
-   Langage de base de données - SQL: ANSI X3H2 et ISO/IEC JTC1/SC21/WG3 9075:1992 (SQL-92).  
  
-   Open Group, Data Management: Structured Query Language (SQL), Version 2 (The Open Group, 1996).  
  
 En plus des normes et des guides SQL spécifiques aux fournisseurs, de nombreux livres décrivent SQL, y compris :  
  
-   Date, C. J., avec Darwen, Hugh: *A Guide to the SQL Standard* (Addison-Wesley, 1993).  
  
-   Emerson, Sandra L., Darnovsky, Marcy, et Bowman, Judith S.: *The Practical SQL Handbook* (Addison-Wesley, 1989).  
  
-   Groff, James R. et Weinberg, Paul N.: *Using SQL* (Osborne McGraw-Hill, 1990).  
  
-   Gruber, Martin : *Understanding SQL* (Sybex, 1990).  
  
-   Hursch, Jack L. et Carolyn J.: *SQL, The Structured Query Language* (TAB Books, 1988).  
  
-   Melton, Jim, et Simon, Alan R.: *Understanding the New SQL: A Complete Guide* (Morgan Kaufmann Publishers, 1993).  
  
-   Pascal, Fabian : *SQL et Relational Basics* (M & T Books, 1990).  
  
-   Trimble, J. Harvey, Jr. et Chappell, David: *A Visual Introduction to SQL* (Wiley, 1989).  
  
-   Van der Lans, Rick F.: *Introduction to SQL* (Addison-Wesley, 1988).  
  
-   Vang, Soren: *SQL et Relational Databases* (Microtrend Books, 1990).  
  
-   Viescas, John: *Quick Reference Guide to SQL* (Microsoft Corp., 1989).  
  
 Pour plus d’informations sur le traitement des transactions, voir :  
  
-   Gray, J. N. et Reuter, Andreas: *Transaction Processing: Concepts and Techniques* (Morgan Kaufmann Publishers, 1993).  
  
-   Hackathorn, Richard D.: *Enterprise Database Connectivity* (Wiley & Sons, 1993).  
  
 Pour plus d’informations sur les interfaces de niveau d’appel, les normes suivantes sont disponibles :  
  
-   Open Group, *Data Management: SQL Call Level Interface (CLI), C451* (Open Group, 1995).  
  
-   ISO/IEC 9075-3:1995, Interface de niveau d’appel (SQL/CLI).  
  
 Pour plus d’informations sur ODBC, un certain nombre de livres sont disponibles, y compris:  
  
-   Geiger, Kyle: *Inside ODBC* (Microsoft Press®, 1995).  
  
-   Gryphon, Robert, Charpentier, Luc, Oelschlager, Jon, Shoemaker, Andrew, Cross, Jim, et Lilley, Albert W.: *Using ODBC 2* (Que, 1994).  
  
-   Johnston, Tom and Osborne, Mark: *ODBC Developers Guide* (Howard W. Sams & Company, 1994).  
  
-   Nord, Ken : *Programmation Multi-DBMS windows : Utilisation de CMD, Visual Basic, ODBC, OLE 2 et Tools for DBMS Projects* (John Wiley & Sons, Inc., 1995).  
  
-   Stegman, Michael O., Signore, Robert, and Creamer, John: *The ODBC Solution, Open Database Connectivity in Distributed Environments* (McGraw-Hill, 1995).  
  
-   Welch, Keith: *Using ODBC 2* (Qc, 1994).  
  
-   Whiting, Bill: *Teach Yourself ODBC in Twenty-One Days* (Howard W. Sams & Company, 1994).
