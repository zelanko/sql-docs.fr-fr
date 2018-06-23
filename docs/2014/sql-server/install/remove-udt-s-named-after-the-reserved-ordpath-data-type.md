---
title: Supprimez les UDT&#39;s nommée d’après le type de données ORDPATH | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 474e910a-6abb-4e28-acc2-055338c011d4
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c2821e47e91bc3d8c91ecf4de7e2efc2f37f881c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042837"
---
# <a name="remove-udt39s-named-after-the-reserved-ordpath-data-type"></a>Supprimez les UDT&#39;s nommée d’après le type de données ORDPATH
  Le Conseiller de mise à niveau a détecté un type défini par l'utilisateur (UDT) nommé d'après un terme réservé pour le type de donnée `ORDPATH`.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les termes utilisés pour les types de données intégrés ne doivent pas être utilisés comme noms pour le Common Language Runtime (CLR) ou types définis par l'utilisateur (UDT) d'alias.  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez le type défini par l'utilisateur qui est nommé d'après le type de données et recrée le type défini par l'utilisateur avec un nom non réservé.  
  
## <a name="external-resources"></a>Ressources externes  
 [Création d’un Type défini par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  