---
title: Supprimer l’UDT&#39;s nommées après les types de données de DATE et d’heure réservés | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 827f060b309a7a620fd448554b074f45d78d3cb0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059139"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a>Supprimer l’UDT&#39;s nommées après les types de données de DATE et d’heure réservés
  Le Conseiller de mise à niveau a détecté un type défini par l'utilisateur (UDT) nommé d'après un terme a réservé pour les types de donnée `date` ou `time`.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les termes utilisés pour les types de données ne doivent pas être utilisés comme noms pour le Common Language Runtime (CLR) ou les types définis par l'utilisateur (UDT) d'alias.  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez le type défini par l'utilisateur qui est nommé d'après le type de données et recrée le type défini par l'utilisateur avec un nom non réservé.  
  
  
