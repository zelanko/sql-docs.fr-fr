---
title: Supprimez les UDT dont le nom après les types de données GEOMETRY et GEOGRAPHY réservés | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f93b179da229793c65db452e4f38bb1f08fbfad1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135249"
---
# <a name="remove-udts-named-after-the-reserved-geometry-and-geography-data-types"></a>Supprimer des types définis par l'utilisateur nommés d'après les types de données réservés GEOMETRY et GEOGRAPHY
  Le Conseiller de mise à niveau a détecté un type défini par l'utilisateur (UDT) nommé d'après un terme a réservé pour les types de donnée `geometry` ou `geography`. Les types de données `geometry` et `geography` font partie de la nouvelle fonctionnalité de données spatiales.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les termes utilisés pour les types de données spatiales ne doivent pas être utilisés comme noms pour le Common Language Runtime (CLR) ou types définis par l'utilisateur (UDT) d'alias.  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez le type défini par l'utilisateur qui est nommé d'après le type de données et recrée le type défini par l'utilisateur avec un nom non réservé.  
  
## <a name="external-resources"></a>Ressources externes  
 [Création d’un type défini par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
