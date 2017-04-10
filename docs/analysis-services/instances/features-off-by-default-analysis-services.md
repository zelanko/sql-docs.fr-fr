---
title: "Fonctionnalit&#233;s d&#233;sactiv&#233;es par d&#233;faut (Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 5
---
# Fonctionnalit&#233;s d&#233;sactiv&#233;es par d&#233;faut (Analysis Services)
  Une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est conçue de façon à être sécurisée par défaut. Par conséquent, les fonctionnalités qui pourraient compromettre la sécurité sont désactivées par défaut. Les fonctionnalités suivantes sont désactivées après leur installation et doivent être activées explicitement si vous voulez les utiliser.  
  
## Liste des fonctionnalités  
 Pour activer les fonctionnalités suivantes, connectez-vous à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Cliquez avec le bouton droit sur le nom de l’instance, puis sélectionnez **Facettes**. Vous pouvez également activer ces fonctionnalités via les propriétés du serveur, comme décrit dans la section suivante.  
  
-   Requêtes d'exploration de données ad hoc (OpenRowset)  
  
-   Objets liés (Vers)  
  
-   Objets liés (De)  
  
-   Écouter uniquement les connexions locales  
  
-   Fonctions définies par l'utilisateur  
  
## Propriétés du serveur  
 Les autres fonctionnalités qui sont désactivées par défaut peuvent être activées via les propriétés du serveur. Se connecter à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Cliquez avec le bouton droit sur le nom de l’instance, puis sélectionnez **Propriétés**. Cliquez sur **Général**, puis cliquez sur **Afficher les options avancées** pour afficher une liste de propriétés plus longue.  
  
-   Requêtes d'exploration de données ad hoc (OpenRowset)  
  
-   Autoriser les modèles d'exploration de données de session (exploration de données)  
  
-   Objets liés (Vers)  
  
-   Objets liés (De)  
  
-   Fonctions COM définies par l'utilisateur  
  
-   Définitions de traces de boîte noire (modèles).  
  
-   Journalisation des requêtes  
  
-   Écouter uniquement les connexions locales  
  
-   XML binaire  
  
-   Compression  
  
-   Affinité de groupe. Pour plus d'informations, consultez [Thread Pool Properties](../../analysis-services/server-properties/thread-pool-properties.md) .  
  
  