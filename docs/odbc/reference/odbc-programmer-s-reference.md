---
title: Guide de référence du programmeur ODBC&#39;s | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280509"
---
# <a name="odbc-programmer39s-reference"></a>Guide de référence du programmeur ODBC&#39;s
Le *Guide de référence du programmeur ODBC* contient les sections suivantes.  
  
-   [Nouveautés d’odbc 3,8](../../odbc/reference/what-s-new-in-odbc-3-8.md) répertorie les nouvelles fonctionnalités ODBC qui ont été ajoutées dans le kit de développement logiciel (SDK) Windows 8.  
  
-   L' [exemple de programme ODBC](../../odbc/reference/sample-odbc-program.md) présente un exemple de programme ODBC.  
  
-   [Introduction à ODBC](../../odbc/reference/introduction-to-odbc.md) fournit un bref historique des langage SQL et ODBC, ainsi que des informations conceptuelles sur l’interface ODBC.  
  
-   Le [développement d’applications](../../odbc/reference/develop-app/developing-applications.md) contient des informations sur le développement d’applications qui utilisent l’interface ODBC et les pilotes qui l’implémentent.  
  
-   [L’installation et la configuration de logiciels ODBC](../../odbc/reference/install/installing-and-configuring-the-odbc-software.md) fournissent des informations sur l’installation et une référence de fonction DLL d’installation.  
  
-   Le [développement d’un pilote ODBC](../../odbc/reference/develop-driver/developing-an-odbc-driver.md) contient des informations sur l’écriture d’un pilote.  
  
-   La [référence d’API](../../odbc/reference/syntax/odbc-reference.md) contient la syntaxe et les informations sémantiques pour toutes les fonctions ODBC.  
  
-   Les [annexes ODBC](../../odbc/reference/appendixes/odbc-appendixes.md) contiennent des détails techniques et des tables de référence pour les codes d’erreur ODBC, les types de données et la grammaire SQL.  
  
## <a name="working-with-the-odbc-documentation"></a>Utilisation de la documentation ODBC  
 L’interface ODBC est conçue pour une utilisation avec le langage de programmation C. L’utilisation de l’interface ODBC s’étend sur trois domaines : les instructions SQL, les appels de fonctions ODBC et la programmation en C. Cette documentation suppose les points suivants :  
  
-   Connaissances pratiques du langage de programmation C.  
  
-   Connaissance générale des SGBD et connaissance de SQL.  
  
 Les conventions typographiques suivantes sont utilisées.  
  
|Format|Utilisé pour|  
|------------|--------------|  
|SELECT * FROM|Les lettres majuscules indiquent les instructions SQL, les noms de macro et les termes utilisés au niveau de la commande du système d’exploitation.|  
|`RETCODE SQLFetch(hdbc)`|La police à espacement fixe est utilisée pour les exemples de lignes de commande et de code de programme.|  
|*argument*|Les mots en italique indiquent les arguments de programmation, les informations que l’utilisateur ou l’application doit fournir, ou l’accentuation des mots.|  
|**SQLEndTran**|Le type Bold indique que la syntaxe doit être tapée exactement comme indiqué, y compris les noms de fonctions.|  
|&#124;|Une barre verticale sépare deux choix s’excluant mutuellement dans une ligne de syntaxe.|  
|...|Les points de suspension indiquent que les arguments peuvent être répétés plusieurs fois.|  
|. . .|Une colonne de trois points indique la continuation des lignes de code précédentes.|  
  
## <a name="about-the-code-examples"></a>À propos des exemples de code  
 Les exemples de code de ce guide sont conçus uniquement à des fins d’illustration. Étant donné qu’elles sont écrites principalement pour illustrer les principes ODBC, l’efficacité a parfois été définie de façon plus claire dans l’intérêt de la clarté. En outre, des sections de code entières ont parfois été omises par souci de clarté. Celles-ci incluent les définitions des fonctions non ODBC (les fonctions dont les noms ne commencent pas par « SQL ») et la plupart de la gestion des erreurs.  
  
 Tous les exemples de code utilisent des chaînes ANSI et le même schéma de base de données, qui est affiché au début des [fonctions de catalogue](../../odbc/reference/develop-app/catalog-functions.md).  
  
## <a name="recommended-reading"></a>Lecture recommandée  
 Pour plus d’informations sur SQL, les normes suivantes sont disponibles :  
  
-   Langage de base de données SQL avec amélioration de l’intégrité, ANSI, 1989 ANSI X 3.135-1989.  
  
-   Langue de base de données SQL : ANSI X3H2 et ISO/IEC JTC1/SC21/WG3 9075:1992 (SQL-92).  
  
-   Ouvrez groupe, Gestion des données : langage SQL (SQL), version 2 (groupe ouvert, 1996).  
  
 Outre les normes et les guides SQL spécifiques aux fournisseurs, de nombreux livres décrivent SQL, notamment :  
  
-   Date, C. J., avec Darwen, Hugh : *Guide de la norme SQL* (Addison-Wesley, 1993).  
  
-   Emerson, Sandra L., Darnovsky, Marcy et Bowman, Judith S. : *The pratique SQL Handbook* (Addison-Wesley, 1989).  
  
-   Groff, James R. et Weinberg, Paul N. : *utilisation de SQL* (Osborne McGraw-Hill, 1990).  
  
-   Gruber, Martin : *comprendre SQL* (Sybex, 1990).  
  
-   Hursch, Jack L. et Carolyn J. : *SQL, le langage SQL* (livres d’onglets, 1988).  
  
-   Melton, Jim et Simon, Alan R. : *Présentation du nouveau guide SQL : A complet* (Morgan Kaufmann Publishers, 1993).  
  
-   Pascal, Fabian : *SQL et principes de base relationnels* (M & T Books, 1990).  
  
-   Trimble, J. Harvey, Jr. et Chappell, David : *présentation visuelle de SQL* (Wiley, 1989).  
  
-   Van der LAN, Rick F. : *Introduction à SQL* (Addison-Wesley, 1988).  
  
-   Vang, Soren : *bases de données SQL et relationnelles* (livres de microtendance, 1990).  
  
-   Viescas, John : *Guide de référence rapide de SQL* (Microsoft Corp., 1989).  
  
 Pour plus d’informations sur le traitement des transactions, consultez :  
  
-   Gris, J. N. et Reuter, Andreas : *traitement des transactions : concepts et techniques* (Kaufmann, éditeurs, 1993).  
  
-   Hackathorn, Richard D. : *Enterprise Database Connectivity* (Wiley & fils, 1993).  
  
 Pour plus d’informations sur les interfaces de niveau appel, les normes suivantes sont disponibles :  
  
-   Ouvrez groupe, *gestion des données : interface de niveau d’appel (CLI) SQL, C451* (ouvrir le groupe, 1995).  
  
-   ISO/IEC 9075-3:1995, interface de niveau d’appel (SQL/CLI).  
  
 Pour plus d’informations sur ODBC, un certain nombre de livres sont disponibles, notamment :  
  
-   Geiger, Kyle : *Inside ODBC* (Microsoft Press®, 1995).  
  
-   Gryphon, Robert, charpentier, Luc, Oelschlager, Jon, Shoemaker, Andrew, Cross, Jim et Lilley, Albert W. : *using ODBC 2* (que, 1994).  
  
-   Johnston, Tom et Osborne, Mark : *Guide des développeurs ODBC* (Howard W. Sams & Company, 1994).  
  
-   Nord, Ken : *programmation Multisgbd Windows : utilisation de C++, Visual Basic, ODBC, OLE 2 et outils pour les projets SGBD* (John Wiley & fils, Inc., 1995).  
  
-   Stegman, Michael O., Signore, Robert et Creamer, John : *la solution ODBC, Open Database Connectivity dans les environnements distribués* (McGraw-Hill, 1995).  
  
-   Welch, Keith : *using ODBC 2* (que, 1994).  
  
-   Merlan, Bill : *Apprenez-vous ODBC en vingt et un jours* (Howard W. Sams & Company, 1994).
