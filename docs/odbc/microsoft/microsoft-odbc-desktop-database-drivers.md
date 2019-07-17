---
title: Pilotes de base de données de bureau de Microsoft ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- Jet-based ODBC drivers [ODBC]
- ODBC desktop database drivers [ODBC], about desktop database drivers
- desktop database drivers [ODBC]
- Jet-based ODBC drivers [ODBC], about Jet-based ODBC drivers
- desktop database drivers [ODBC], about desktop database drivers
ms.assetid: 4e505c65-a8dd-4283-ae28-313d8a3aa046
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8ee91a2e544babdd02a22bcbe426a7fb0d770f66
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68109682"
---
# <a name="microsoft-odbc-desktop-database-drivers"></a>Pilotes Microsoft ODBC pour les bases de données de poste de travail
ODBC est une API qui utilise le langage SQL (Structured Query) comme langue d’accès de base de données. Vous pouvez accéder à un large éventail de systèmes de gestion de base de données (SGBD) avec le même code de source ODBC directement incorporé dans le code source d’une application. Avec les pilotes de base de données Microsoft ODBC Desktop, un utilisateur d’une application compatible ODBC peut ouvrir, la requête et mettre à jour une base de données de bureau via l’interface ODBC.  
  
 Les pilotes de base de données Microsoft ODBC Desktop sont un ensemble de basées sur Jet de Microsoft des pilotes ODBC. Tandis que les pilotes de base de données de bureau Microsoft ODBC 2.0 inclut les pilotes 16 bits et 32 bits, les versions 3.0 et versions ultérieures incluent seuls les pilotes 32 bits qui fonctionnent sur Windows 95 ou version ultérieure, Windows NT Workstation ou version 4.0, Windows 2000 Professionnel ou Windows 2000 Server Serveur. Ces pilotes permettent d’accéder aux types de sources de données suivants :  
  
-   Microsoft Access  
  
-   Microsoft Excel  
  
-   Paradox  
  
-   dBASE  
  
-   Text  
  
 Consultez [pilote ODBC Visual FoxPro](../../odbc/microsoft/visual-foxpro-odbc-driver.md) pour obtenir une documentation détaillée sur le pilote ODBC de® Microsoft Visual FoxPro.  
  
> [!NOTE]  
>  Accès à d’autres sources de données, tels que Lotus 1-2-3, Microsoft Exchange et HTML, est activé par les pilotes installables ISAM (IISAM). Pour plus d’informations sur ces pilotes, consultez « L’accès à des données externes » dans le *de référence du programmeur moteur Microsoft Jet de base de données*. Base de données de bureau ODBC Drivers 4.0 ne gèrent pas les formats de données Btrieve et EMS.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Architecture des pilotes pour les bases de données de poste de travail](../../odbc/microsoft/desktop-database-drivers-architecture.md)  
  
-   [Historique des pilotes pour les bases de données de poste de travail](../../odbc/microsoft/history-of-the-desktop-database-drivers.md)  
  
-   [Prise en charge du produit](../../odbc/microsoft/product-support.md)  
  
-   [Implémentation des pilotes pour les bases de données de poste de travail](../../odbc/microsoft/implementing-desktop-database-drivers.md)  
  
-   [Considérations sur la programmation du pilote Microsoft Access](../../odbc/microsoft/microsoft-access-driver-programming-considerations.md)  
  
-   [Considérations sur la programmation du pilote Microsoft Excel](../../odbc/microsoft/microsoft-excel-driver-programming-considerations.md)  
  
-   [Considérations sur la programmation du pilote Paradox](../../odbc/microsoft/paradox-driver-programming-considerations.md)  
  
-   [Considérations sur la programmation du pilote dBASE](../../odbc/microsoft/dbase-driver-programming-considerations.md)  
  
-   [Considérations sur la programmation du pilote de fichier texte](../../odbc/microsoft/text-file-driver-programming-considerations.md)  
  
-   [Grammaire SQL ODBC supplémentaire prise en charge](../../odbc/microsoft/additional-supported-odbc-sql-grammar.md)  
  
-   [Limitations](../../odbc/microsoft/limitations.md)  
  
-   [Erreurs ODBC](../../odbc/microsoft/odbc-errors.md)  
  
-   [Fonctions de l’API ODBC prises en charge](../../odbc/microsoft/supported-odbc-api-functions.md)
