---
title: Configuration du réseau de cluster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- cluster network selection, Setup
- cluster network selection
ms.assetid: 579482ef-a023-45b2-9176-b4a4188adf9d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3cd117a9f873de13938d8a6946faf4f1c00d522d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63064421"
---
# <a name="cluster-network-configuration"></a>Configuration du réseau du cluster
  Utilisez la page **Sélection du réseau du cluster** pour spécifier les ressources réseau de votre instance de cluster de basculement.  
  
## <a name="options"></a>Options  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Nom réseau du cluster de basculement** : il s’agit du nom identifiant votre instance de cluster de basculement sur le réseau.  
  
 **Paramètres réseau** : spécifiez le type IP et l’adresse IP de votre instance de cluster de basculement.  
  
 Lors des opérations Ajouter un nœud et Supprimer un nœud, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche une liste en lecture seule des adresses IP existantes pour le cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Installation intégrée :  
  
    -   Si vous ajoutez un nœud qui prend en charge un ensemble identique des sous-réseaux de réseau pris en charge par les nœuds existants du cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , aucune adresse IP supplémentaire ne peut être ajoutée. Le paramètre de dépendance reste inchangé.  
  
    -   Si vous ajoutez un nœud qui prend en charge un sous-ensemble des sous-réseaux pris en charge par les nœuds existants du cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , aucune ressource d'adresse IP supplémentaire ne peut être ajoutée. La dépendance de ressource d'adresse IP est définie sur OR pour prendre en compte le fait que toutes les adresses IP spécifiées ne sont pas valides sur l'ensemble des nœuds de cluster.  
  
    -   Si vous ajoutez un nœud qui prend en charge des sous-réseaux en plus de ceux déjà pris en charge par les nœuds existants sur le cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous avez la possibilité d'ajouter de nouvelles adresses IP valides. Si de nouvelles adresses IP sont spécifiées, la dépendance de ressource d'adresse IP est définie sur OR pour prendre en compte le fait que toutes les adresses IP spécifiées ne sont pas valides sur l'ensemble des nœuds de cluster.  
  
    -   Si vous ajoutez un nœud qui prend en charge des sous-réseaux de réseau supplémentaires, mais aucun des sous-réseaux pris en charge par les nœuds existants sur le cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez ajouter des adresses IP supplémentaires. La dépendance de ressource d'adresse IP est définie sur OR pour prendre en compte le fait que toutes les adresses IP spécifiées ne sont pas valides sur l'ensemble des nœuds de cluster.  
  
-   Installation avancée : Pendant l’étape de fin de l’installation, spécifiez l’adresse IP pour tous les nœuds et sous-réseaux de votre instance de cluster de basculement. Vous pouvez spécifier plusieurs adresses IP pour un cluster de basculement de sous-réseaux multiples, mais une seule adresse IP par sous-réseau est prise en charge. Chaque nœud préparé doit être le propriétaire d'au moins une adresse IP. Si vous avez plusieurs sous-réseaux dans votre cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous êtes invité à définir la dépendance de ressource d'adresse IP sur OR. Supprimer un nœud :  
  
    -   Si les adresses IP restantes sont prises en charge sur tous les nœuds restants, vous êtes invité à définir la dépendance de ressource d'adresse IP sur AND.  
  
    -   Si les adresses IP restantes ne sont pas prises en charge sur tous les nœuds restants, la dépendance de ressource d'adresse IP reste sur OR.  
  
  
