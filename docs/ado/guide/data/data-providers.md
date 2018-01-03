---
title: "Fournisseurs de données | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b424a116282c7c1edcfa06f22fc72f32a7e0fcda
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="data-providers"></a>Fournisseurs de données
Fournisseurs de données représentent diverses sources de données telles que les bases de données SQL, fichiers séquentiels indexés, des feuilles de calcul, banques de documents et fichiers de la messagerie. Fournisseurs présentent les données de façon uniforme en utilisant une abstraction commune appelée l’ensemble de lignes.  
  
 ADO est puissant et flexible, car il peut se connecter à plusieurs fournisseurs de données et exposent toujours le même modèle de programmation, indépendamment des fonctionnalités spécifiques de n’importe quel fournisseur donné. Toutefois, étant donné que chaque fournisseur de données est unique, comment votre application interagit avec ADO varie par fournisseur de données.  
  
 Par exemple, les fonctionnalités du fournisseur OLE DB pour SQL Server, ce qui permet d’accéder aux bases de données Microsoft SQL Server, sont très différentes de ceux du fournisseur Microsoft OLE DB pour Internet Publishing, qui est utilisé pour accéder au fichier magasins de sur un serveur Web.
