---
title: Désactiver des fonctionnalités par défaut (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9bcb28d99f8d06430ca1ff68563e8ab8c075929f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37214172"
---
# <a name="features-off-by-default-analysis-services"></a>Fonctionnalités désactivées par défaut (Analysis Services)
  Une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est conçue de façon à être sécurisée par défaut. Par conséquent, les fonctionnalités qui pourraient compromettre la sécurité sont désactivées par défaut. Les fonctionnalités suivantes sont désactivées après leur installation et doivent être activées explicitement si vous voulez les utiliser.  
  
## <a name="feature-list"></a>Liste des fonctionnalités  
 Pour activer les fonctionnalités suivantes, connectez-vous à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Cliquez avec le bouton droit sur le nom de l’instance, puis sélectionnez **Facettes**. Vous pouvez également activer ces fonctionnalités via les propriétés du serveur, comme décrit dans la section suivante.  
  
-   Requêtes d'exploration de données ad hoc (OpenRowset)  
  
-   Objets liés (Vers)  
  
-   Objets liés (De)  
  
-   Écouter uniquement les connexions locales  
  
-   Fonctions définies par l'utilisateur  
  
## <a name="server-properties"></a>Propriétés du serveur  
 Les autres fonctionnalités qui sont désactivées par défaut peuvent être activées via les propriétés du serveur. Se connecter à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Cliquez avec le bouton droit sur le nom de l’instance, puis sélectionnez **Propriétés**. Cliquez sur **Général**, puis cliquez sur **Afficher les options avancées** pour afficher une liste de propriétés plus longue.  
  
-   Requêtes d'exploration de données ad hoc (OpenRowset)  
  
-   Autoriser les modèles d'exploration de données de session (exploration de données)  
  
-   Objets liés (Vers)  
  
-   Objets liés (De)  
  
-   Fonctions COM définies par l'utilisateur  
  
-   Définitions de traces de boîte noire (modèles).  
  
-   Journalisation des requêtes  
  
-   Écouter uniquement les connexions locales  
  
-   XML binaire  
  
-   Compression  
  
-   Affinité de groupe. Pour plus d'informations, consultez [Thread Pool Properties](../server-properties/thread-pool-properties.md) .  
  
  
