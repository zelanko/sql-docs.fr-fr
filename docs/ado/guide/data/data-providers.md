---
title: Fournisseurs de données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c3b8a4ac0da80303a63bd62f7b4d6f51faab1fb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472566"
---
# <a name="data-providers"></a>Fournisseurs de données
Fournisseurs de données représentent diverses sources de données telles que les bases de données SQL, des fichiers à accès séquentiel indexé, des feuilles de calcul, banques de documents et fichiers de courrier. Fournisseurs présentent les données uniformément à l’aide d’une abstraction commune appelée l’ensemble de lignes.  
  
 ADO est puissant et flexible, car il peut se connecter à plusieurs fournisseurs de données et continuer à exposer le même modèle de programmation, indépendamment des fonctionnalités spécifiques de n’importe quel fournisseur donné. Cependant, étant donné que chaque fournisseur de données est unique, comment votre application interagit avec ADO varie par fournisseur de données.  
  
 Par exemple, les fonctionnalités du fournisseur OLE DB pour SQL Server, qui est utilisé pour accéder aux bases de données Microsoft SQL Server, sont très différentes de celles du fournisseur Microsoft OLE DB pour Internet Publishing, qui est utilisé pour accéder au fichier magasins sur un serveur Web.
