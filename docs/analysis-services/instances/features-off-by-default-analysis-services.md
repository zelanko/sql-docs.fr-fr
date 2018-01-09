---
title: "Désactiver les fonctionnalités par défaut (Analysis Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 21ff5e0b59b3e14df550bb580b1c59dde449452e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="features-off-by-default-analysis-services"></a>Fonctionnalités désactivées par défaut (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est conçu pour être sécurisés par défaut. Par conséquent, les fonctionnalités qui pourraient compromettre la sécurité sont désactivées par défaut. Les fonctionnalités suivantes sont désactivées après leur installation et doivent être activées explicitement si vous voulez les utiliser.  
  
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
  
-   Affinité de groupe. Pour plus d'informations, consultez [Thread Pool Properties](../../analysis-services/server-properties/thread-pool-properties.md) .  
  
  
