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
manager: jroth
ms.openlocfilehash: 30d1e1515ed3e84640fe1ca004cb7cbf4383ce97
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718718"
---
# <a name="data-providers"></a>Fournisseurs de données
Fournisseurs de données représentent diverses sources de données telles que les bases de données SQL, des fichiers à accès séquentiel indexé, des feuilles de calcul, banques de documents et fichiers de courrier. Fournisseurs présentent les données uniformément à l’aide d’une abstraction commune appelée l’ensemble de lignes.  
  
 ADO est puissant et flexible, car il peut se connecter à plusieurs fournisseurs de données et continuer à exposer le même modèle de programmation, indépendamment des fonctionnalités spécifiques de n’importe quel fournisseur donné. Cependant, étant donné que chaque fournisseur de données est unique, comment votre application interagit avec ADO varie par fournisseur de données.  
  
 Par exemple, les fonctionnalités du fournisseur OLE DB pour SQL Server, qui est utilisé pour accéder aux bases de données Microsoft SQL Server, sont très différentes de celles du fournisseur Microsoft OLE DB pour Internet Publishing, qui est utilisé pour accéder au fichier magasins sur un serveur Web.
