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
author: rothja
ms.author: jroth
ms.openlocfilehash: 6dfb672b57b95224cf6ff056c3298c7c8a437d2a
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761105"
---
# <a name="data-providers"></a>Fournisseurs de données
Les fournisseurs de données représentent diverses sources de données telles que les bases de données SQL, les fichiers séquentiels indexés, les feuilles de calcul, les magasins de documents et les fichiers de messagerie. Les fournisseurs exposent les données uniformément à l’aide d’une abstraction commune appelée ensemble de lignes.  
  
 ADO est puissant et flexible, car il peut se connecter à n’importe quel autre fournisseur de données et exposer toujours le même modèle de programmation, quelles que soient les fonctionnalités spécifiques d’un fournisseur donné. Toutefois, étant donné que chaque fournisseur de données est unique, la façon dont votre application interagit avec ADO varie selon le fournisseur de données.  
  
 Par exemple, les fonctionnalités du fournisseur OLE DB pour SQL Server, qui est utilisé pour accéder aux bases de données Microsoft SQL Server, sont très différentes de celles du fournisseur Microsoft OLE DB pour la publication Internet, qui est utilisée pour accéder aux magasins de fichiers sur un serveur Web.
