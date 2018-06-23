---
title: Supprimez les UDT nommés d’après les types de données GEOMETRY et GEOGRAPHY réservés | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d772f880e1ad88c6423d0a34f71d1a75205169f7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053449"
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
 [Création d’un Type défini par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [Présentation des types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  