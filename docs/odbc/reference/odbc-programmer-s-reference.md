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
manager: craigg
ms.openlocfilehash: 7fc5177fda3562efe4561f9d165629419f8a629b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850921"
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
 L’interface ODBC est conçue pour une utilisation avec le langage de programmation C. Utilisation de l’interface ODBC s’étend sur trois domaines : les instructions SQL, ODBC appels de fonction et programmation en C. Cette documentation suppose ce qui suit :  
  
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
  
-   Langue de base de données, SQL d’avec intégrité amélioration, ANSI, 1989 ANSI X3.135-1989.  
  
-   Langue de base de données, SQL : X3H2 de ANSI et ISO/IEC JTC1/SC21/WG3 9075 : 1992 (SQL-92).  
  
-   Ouvrir le groupe, gestion des données : Structured Query Language (SQL), Version 2 (The Open Group, 1996).  
  
 En plus des normes et des repères de SQL spécifiques au fournisseur, nombreux livres décrivent SQL, y compris :  
  
-   Date, J. C., à avec Darwen, Hugh : *un Guide pour la norme SQL* (Addison-Wesley, 1993).  
  
-   Emerson L. Sandra, Darnovsky, Marcy et Bowman, S. Judith : *le manuel pratique SQL* (Addison-Wesley, 1989).  
  
-   Groff, R. James et Weinberg, N. Paul : *à l’aide de SQL* (Osborne McGraw-Hill, 1990).  
  
-   Gruber, Martin : *comprendre SQL* (Sybex, 1990).  
  
-   Hursch, Jack l et J. Caroline : *SQL, le langage de requête structuré* (onglet Books, 1988).  
  
-   Melton, Jim et Simon, R. Alan : *comprendre le nouveau SQL : un Guide complet* (Morgan Kaufmann Publishers, 1993).  
  
-   Pascal, Fabian avoir : *SQL et les principes de base relationnelle* (M & T Books, 1990).  
  
-   Trimble, J. Harvey, Jr. et Chappell, David : *une présentation visuelle de SQL* (Wiley, 1989).  
  
-   Réseaux locaux van der, Rick F. : *Introduction to SQL* (Addison-Wesley, 1988).  
  
-   Vang, Soren : *SQL et les bases de données relationnelles* (Microtrend Books, 1990).  
  
-   Viescas, John : *Guide de référence rapide SQL* (Microsoft Corp., 1989).  
  
 Pour plus d’informations sur le traitement des transactions, consultez :  
  
-   Gris, N. J. et Reuter, Andreas : *traitement des transactions : Concepts et Techniques* (Morgan Kaufmann Publishers, 1993).  
  
-   Hackathorn, D. Richard : *connectivité de base de données d’entreprise* (Wiley & Sons, 1993).  
  
 Pour plus d’informations sur les Interfaces de niveau d’appel, les normes suivantes sont disponibles :  
  
-   Open Group, *gestion des données : SQL niveau Interface d’appel (CLI), C451* (Open Group, 1995).  
  
-   ISO/IEC 9075-3:1995, Interface de niveau d’appel (SQL/CLI).  
  
 Pour plus d’informations sur ODBC, un nombre de livres est disponible, notamment :  
  
-   GEIGER, Kyle : *dans ODBC* (Microsoft Press®, 1995).  
  
-   Gryphon, Robert, Charpentier, Luc, Oelschlager, Jon, Shoemaker, Andrew, Cross, Jim et Lilley, W. Albert : *à l’aide d’ODBC 2* (Que, 1994).  
  
-   Johnston, Tom et Osborne, marquer : *Guide du développeur ODBC* (Howard W. Sams & Company, 1994).  
  
-   Nord, Ken : *Windows Multi-DBMS programmation : à l’aide de C++, Visual Basic, ODBC, OLE 2 et outils pour les projets de SGBD* (John Wiley & Sons, Inc., 1995).  
  
-   Stegman, Michael o, Signore, Robert et Creamer, John : *la Solution ODBC, Open Database Connectivity dans des environnements distribués* (McGraw-Hill, 1995).  
  
-   Welch, Keith : *à l’aide d’ODBC 2* (Que, 1994).  
  
-   Merlan, facture : *Teach Yourself ODBC dans les 21 jours* (Howard W. Sams & Company, 1994).
