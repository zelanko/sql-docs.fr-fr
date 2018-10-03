---
title: Supprimez les UDT&#39;s nommé d’après le type de données ORDPATH | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b98fa9765a40d3eb9c05852e9c20c05c4bb818a0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209269"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a>Supprimez les UDT&#39;s nommé d’après le type de données ORDPATH
  Le Conseiller de mise à niveau a détecté un type défini par l'utilisateur (UDT) nommé d'après un terme réservé pour le type de donnée `ORDPATH`.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les termes utilisés pour les types de données intégrés ne doivent pas être utilisés comme noms pour le Common Language Runtime (CLR) ou types définis par l'utilisateur (UDT) d'alias.  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez le type défini par l'utilisateur qui est nommé d'après le type de données et recrée le type défini par l'utilisateur avec un nom non réservé.  
  
## <a name="external-resources"></a>Ressources externes  
 [Création d’un type défini par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
