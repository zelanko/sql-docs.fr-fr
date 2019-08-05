---
title: Profils de l’Agent (agent unique) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.profiles.perfprofileagentname.f1
helpviewer_keywords:
- Agent Profile dialog box
ms.assetid: 22713555-c496-4ce1-8ec7-4ae75cfadca8
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 08a8362ab1cdf55af1c3735ee9ab27fb9991b07e
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770833"
---
# <a name="agent-profiles-single-agent"></a>Profils de l'Agent (agent unique)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  La boîte de dialogue **Profils de l'Agent** permet de gérer les profils d'un agent. Les profils d'agent permettent de gérer aisément les paramètres d'exécution de chaque agent. Chaque agent possède un profil par défaut tandis que certains ont des profils prédéfinis supplémentaires. Par exemple, l'Agent de fusion possède un profil « liaison lente » conçu pour les connexions à faible bande passante. Les profils prédéfinis suffisent pour la plupart des applications, mais vous pouvez également créer des profils définis par l'utilisateur, qui vous permettent de personnaliser le comportement de l'agent.  
  
## <a name="options"></a>Options  
 **Valeur par défaut pour nouveau**  
 Sélectionnez le profil à utiliser lorsque des travaux sont créés pour un agent d'un type donné. Par exemple, si vous créez plusieurs abonnements à une publication de fusion, le travail de l'Agent de fusion pour chaque abonnement utilisera le profil sélectionné. Si vous souhaitez modifier le profil de travaux existants, sélectionnez un profil, puis cliquez sur **Modifier les Agents existants**.  
  
 **Name**  
 Nom du profil  
  
 **Type**  
 Type de profil : **Utilisateur** (défini par l’utilisateur) ou **Système** (prédéfini).  
  
 **Propriétés (...)**  
 Cliquez sur cette option pour voir les valeurs utilisées pour chaque paramètre dans le profil de l'agent.  
  
 **Nouveau**  
 Cliquez sur ce bouton pour créer un profil.  
  
 **Supprimer**  
 Sélectionnez un profil défini par l'utilisateur, puis cliquez sur **Supprimer** pour le supprimer. Les profils prédéfinis ne peuvent pas être supprimés.  
  
 **Modifier les Agents existants**  
 Sélectionnez un profil, puis cliquez sur **Modifier les Agents existants** afin d'indiquer que tous les travaux existants d'un agent d'un type donné doivent utiliser le profil sélectionné. Par exemple, si vous avez créé plusieurs abonnements à une publication de fusion et que vous souhaitez modifier le profil afin de spécifier que le travail d'Agent de fusion de chaque abonnement doit utiliser le **Profil de liaison lente de l'agent**, sélectionnez ce profil, puis cliquez sur **Modifier les Agents existants**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des profils d’Agent de réplication](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Profils de l’Agent de réplication](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  
