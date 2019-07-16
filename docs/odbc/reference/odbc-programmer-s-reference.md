---
title: Programmeur ODBC&#39;s référence | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fd729956ee7bb1fccf7a8fceb7a435042df4df7e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111195"
---
# <a name="odbc-programmer39s-reference"></a>Programmeur ODBC&#39;s référence
Le *de référence du programmeur ODBC* contient les sections suivantes.  
  
-   [What ' s New in ODBC 3.8](../../odbc/reference/what-s-new-in-odbc-3-8.md) répertorie les nouvelles fonctionnalités ODBC qui ont été ajoutées dans le Kit de développement logiciel Windows 8.  
  
-   [Exemple de programme ODBC](../../odbc/reference/sample-odbc-program.md) présente un exemple de programme ODBC.  
  
-   [Introduction à ODBC](../../odbc/reference/introduction-to-odbc.md) fournit un bref historique de Structured Query Language, ODBC et des informations conceptuelles sur l’interface ODBC.  
  
-   [Développement d’Applications](../../odbc/reference/develop-app/developing-applications.md) contient des informations sur le développement d’applications qui utilisent l’interface ODBC et les pilotes qui l’implémentent.  
  
-   [Installation et configuration logicielle ODBC](../../odbc/reference/install/installing-and-configuring-the-odbc-software.md) fournit des informations sur une installation et de référence des fonctions DLL.  
  
-   [Développement d’un pilote ODBC](../../odbc/reference/develop-driver/developing-an-odbc-driver.md) contient des informations sur l’écriture d’un pilote.  
  
-   [Référence de l’API](../../odbc/reference/syntax/odbc-reference.md) contient la syntaxe et les informations sémantiques relatives à toutes les fonctions ODBC.  
  
-   [Annexes ODBC](../../odbc/reference/appendixes/odbc-appendixes.md) contiennent des détails techniques et référencer des tables pour les codes d’erreur ODBC, de types de données et de grammaire SQL.  
  
## <a name="working-with-the-odbc-documentation"></a>Utilisation de la Documentation ODBC  
 L’interface ODBC est conçue pour une utilisation avec le langage de programmation C. Utilisation de l’interface ODBC s’étend sur trois domaines : Instructions SQL, appels de fonction ODBC et programmation en C. Cette documentation suppose ce qui suit :  
  
-   Une connaissance pratique du langage de programmation C.  
  
-   Les connaissances générales DBMS et vous familiariser avec SQL.  
  
 Les conventions typographiques suivantes sont utilisées.  
  
|Format|Utilisé pour|  
|------------|--------------|  
|SÉLECTIONNEZ * À PARTIR DE|Lettres majuscules indiquent des instructions SQL, les noms de macros et termes utilisés au niveau de la commande de système d’exploitation.|  
|`RETCODE SQLFetch(hdbc)`|La police à espacement fixe est utilisée pour les exemples de lignes de commande et du code de programme.|  
|*argument*|Les mots en italique indiquent des arguments par programmation, les informations que l’utilisateur ou l’application doit fournir, ou word mettant l’accent.|  
|**SQLEndTran**|En gras que syntaxe doit être tapée exactement comme indiqué, y compris les noms de fonction.|  
|&#124;|Une barre verticale sépare deux choix qui s’excluent mutuellement dans une ligne de syntaxe.|  
|...|Points de suspension indique que les arguments peuvent être répétées plusieurs fois.|  
|. . .|Une colonne de trois points indique la continuation de lignes de code précédentes.|  
  
## <a name="about-the-code-examples"></a>Sur les exemples de Code  
 Les exemples de code dans ce guide sont conçus uniquement à des fins d’illustration. Car elles sont écrites principalement à illustrer les principes d’ODBC, l’efficacité a parfois été définie pour des raisons de clarté. En outre, des sections entières de code ont parfois été omises par souci de clarté. Citons notamment les définitions de fonctions non-ODBC (fonctions dont les noms ne commencent pas par « SQL ») la plupart des erreurs et des exceptions.  
  
 Tous les exemples de code utilisent des chaînes ANSI et le même schéma de base de données, ce qui est présenté au début de [fonctions de catalogue](../../odbc/reference/develop-app/catalog-functions.md).  
  
## <a name="recommended-reading"></a>Lecture recommandée  
 Pour plus d’informations sur SQL, les normes suivantes sont disponibles :  
  
-   Base de données SQL avec l’intégrité amélioration, ANSI, 1989 ANSI X3.135-1989 - Language.  
  
-   Langue de base de données - SQL : 9075 de : 1992 (SQL-92) X3H2 de ANSI et ISO/IEC JTC1/SC21/WG3.  
  
-   Open Group, gestion des données : Structured Query Language (SQL), Version 2 (The Open Group, 1996).  
  
 En plus des normes et des repères de SQL spécifiques au fournisseur, nombreux livres décrivent SQL, y compris :  
  
-   Date, J. C., à avec Darwen, Hugh : *Un Guide pour la norme SQL* (Addison-Wesley, 1993).  
  
-   Emerson L. Sandra, Darnovsky, Marcy et Bowman, Judith s : *Le manuel pratique SQL* (Addison-Wesley, 1989).  
  
-   Groff, R. James et Weinberg, N. Paul : *À l’aide de SQL* (Osborne McGraw-Hill, 1990).  
  
-   Gruber, Martin : *Présentation de SQL* (Sybex, 1990).  
  
-   Hursch, Jack l et J. Caroline : *SQL, le langage de requête structuré* (onglet Books, 1988).  
  
-   Melton, Jim et Simon, R. Alan : *Comprendre le nouveau SQL : Un Guide complet* (Morgan Kaufmann Publishers, 1993).  
  
-   Pascal, Fabian avoir : *SQL et les principes de base relationnelle* (M & T Books, 1990).  
  
-   Trimble, J. Harvey, Jr. et Chappell, David : *Une présentation visuelle de SQL* (Wiley, 1989).  
  
-   Réseaux locaux van der, Rick F. : *Introduction à SQL* (Addison-Wesley, 1988).  
  
-   Vang, Soren : *SQL et les bases de données relationnelles* (Microtrend Books, 1990).  
  
-   Viescas, John : *Guide de référence rapide SQL* (Microsoft Corp., 1989).  
  
 Pour plus d’informations sur le traitement des transactions, consultez :  
  
-   Gris, N. J. et Reuter, Andreas : *Traitement des transactions : Concepts et Techniques* (Morgan Kaufmann Publishers, 1993).  
  
-   Hackathorn, D. Richard : *Connectivité de base de données d’entreprise* (Wiley & Sons, 1993).  
  
 Pour plus d’informations sur les Interfaces de niveau d’appel, les normes suivantes sont disponibles :  
  
-   Open Group, *gestion des données : Appel de niveau Interface SQL (CLI), C451* (Open Group, 1995).  
  
-   ISO/IEC 9075-3:1995, Interface de niveau d’appel (SQL/CLI).  
  
 Pour plus d’informations sur ODBC, un nombre de livres est disponible, notamment :  
  
-   GEIGER, Kyle : *À l’intérieur de ODBC* (Microsoft Press®, 1995).  
  
-   Gryphon, Robert, Charpentier, Luc, Oelschlager, Jon, Shoemaker, Andrew, Cross, Jim et Lilley, W. Albert : *À l’aide d’ODBC 2* (Que, 1994).  
  
-   Johnston, Tom et Osborne, marque : *Guide du développeur ODBC* (Howard W. Sams & Company, 1994).  
  
-   Nord, Ken : *Programmation de Multi-DBMS Windows : À l’aide de C++, Visual Basic, ODBC, OLE 2 et outils pour les projets de SGBD* (John Wiley & Sons, Inc., 1995).  
  
-   Stegman, Michael o, Signore, Robert et Creamer, John : *La Solution d’ODBC, Open Database Connectivity dans des environnements distribués* (McGraw-Hill, 1995).  
  
-   Welch, Keith : *À l’aide d’ODBC 2* (Que, 1994).  
  
-   Merlan, facture : *TEACH Yourself ODBC dans les 21 jours* (Howard W. Sams & Company, 1994).
