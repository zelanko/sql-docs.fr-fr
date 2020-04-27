---
title: Sécurité de l’agent (Assistant Nouvelle publication) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.agentsecurity.articles.f1
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 555aa4e49887000354e5d31ff5d039a5f0ac75eb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63259158"
---
# <a name="agent-security-new-publication-wizard"></a>Sécurité de l'agent (Assistant Nouvelle publication)
  La page **Sécurité de l'agent** vous permet de spécifier les comptes sous lesquels les agents ci-après s'exécutent et les connexions sont établies aux ordinateurs dans une topologie de réplication :  
  
-   Agent d'instantané pour toutes les publications ;  
  
-   Agent de lecture du journal pour toutes les publications transactionnelles ;  
  
-   Agent de lecture de la file d'attente pour les publications transactionnelles qui autorisent les abonnements pouvant être mis à jour. Le travail de l’Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour cet agent est créé si vous avez spécifié l’option **Publication transactionnelle avec abonnements pouvant être mis à jour** dans la page **Type de publication**, quel que soit le type d’abonnements pouvant être mis à jour que vous utilisez. Pour plus d'informations sur les abonnements pouvant être mis à jour, consultez [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 Pour plus d'informations sur les autorisations requises par les agents et les méthodes préconisées pour la sécurité de la réplication, consultez [Replication Agent Security Model](security/replication-agent-security-model.md) et [Replication Security Best Practices](security/replication-security-best-practices.md).  
  
## <a name="options"></a>Options  
 **Agent d’instantané**  
 Affiché pour toutes les publications. Cliquez sur **Paramètres de sécurité** pour spécifier les paramètres de sécurité dans la boîte de dialogue **Sécurité de l'Agent d'instantané** .  
  
 Cliquez sur **Aide** dans la boîte de dialogue **Sécurité de l'Agent d'instantané** pour obtenir des informations supplémentaires sur les autorisations requises pour les comptes utilisés par l'Agent d'instantané.  
  
 **Agent de lecture du journal**  
 Affiché pour toutes les publications transactionnelles. Cliquez sur **Paramètres de sécurité** pour spécifier les paramètres de sécurité dans la boîte de dialogue **Sécurité de l'Agent de lecture du journal** .  
  
 Cliquez sur **Aide** dans la boîte de dialogue **Sécurité de l'Agent de lecture du journal** pour obtenir des informations supplémentaires sur les autorisations requises pour les comptes utilisés par l'Agent de lecture du journal.  
  
> [!NOTE]  
>  Il existe un Agent de lecture du journal pour chaque base de données publiée utilisant la réplication transactionnelle. Si une publication transactionnelle existe déjà dans la base de données, les paramètres de sécurité sont en lecture seule. Vous pouvez modifier les paramètres dans la boîte de dialogue **Propriétés de la publication** ; toutefois, toutes les publications transactionnelles seront affectées dans la base de données.  
  
 **Agent de lecture de la file d’attente**  
 Affiché pour les publications transactionnelles qui autorisent les abonnements pouvant être mis à jour. Cliquez sur **Paramètres de sécurité** pour spécifier les paramètres de sécurité dans la boîte de dialogue **Sécurité de l'Agent de lecture de la file d'attente** . Une fois l'exécution de cet Assistant terminée, un Agent de lecture de la file d'attente est créé. Sa création ne dépend aucunement de la création d'abonnements mis à jour en file d'attente. Si vous n'envisagez pas de créer des abonnements mis à jour en file d'attente , vous pouvez désactiver ce travail. Cliquez avec le bouton droit sur ce travail (nommé sous la forme : *[\<serveur_publication>].\<entier>* .) dans le dossier **Travaux de l’Agent**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puis cliquez sur **Désactiver**.  
  
 Cliquez sur **Aide** dans la la boîte de dialogue **Sécurité de l'Agent de lecture de la file d'attente** pour obtenir des informations supplémentaires sur les autorisations requises pour les comptes utilisés par l'Agent de lecture de la file d'attente.  
  
> [!NOTE]  
>  Il existe un Agent de lecture de la file d'attente pour chaque base de données de distribution (et pour tous les serveurs de publication qu'il sert). Si une publication transactionnelle qui autorise les abonnements de mise à jour en attente existe déjà sur un serveur de publication, qui utilise une base de données de distribution donnée, les paramètres de sécurité sont en lecture seule. Vous pouvez modifier le compte sous lequel l'Agent de lecture de la file d'attente est exécuté et les connexions sont établies dans la boîte de dialogue **Propriétés du serveur de distribution** . Toutefois, les publications sur tous les serveurs correspondants seront affectées dans la base de données de distribution.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](publish/create-a-publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)   
 [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)   
 [Gérer les connexions et les mots de passe dans la réplication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)  
  
  
