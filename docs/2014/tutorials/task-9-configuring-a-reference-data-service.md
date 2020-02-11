---
title: 'Tâche 9 : configuration d’un service de données de référence | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d0535fce-2bf5-4f6d-b517-ffe6fa13738d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: e4c756463c43ede8c6dae0cda0a184f0ec7f9956
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70154933"
---
# <a name="task-9-configuring-a-reference-data-service"></a>Tâche 9 : Configuration d'un service de données de référence
  Dans cette tâche, vous allez configurer DQS pour utiliser un service de données de référence sur la place de marché Microsoft Azure. Dans la tâche suivante, vous allez configurer le domaine **Validation d'adresses** pour utiliser ce service. Au moment de l’exécution, pendant l’activité de nettoyage, DQS passe les valeurs des domaines dans le domaine de **validation d’adresse** au service pour le nettoyage. Consultez [Configurer DQS pour utiliser des données de référence](https://msdn.microsoft.com/library/hh213070.aspx) pour plus de détails.  
  
1.  Dans la page principale du **Client DQS**, cliquez sur **Configuration** dans le volet **Administration**.  
  
2.  Assurez-vous que l'onglet **Données de référence** est actif.  
  
3.  Dans la zone **Paramètres réseau** , entrez les valeurs appropriées dans les champs **Serveur proxy** et **Port** si vous devez utiliser un serveur proxy pour vous connecter à Internet.  
  
4.  Tapez votre **clé de compte Azure Marketplace** pour le champ **ID de compte DataMarket** .  
  
     ![Compte de service de données de référence d'Azure Data Market](../../2014/tutorials/media/et-configuringareferencedataservice.jpg "Compte de service de données de référence d'Azure Data Market")  
  
5.  Cliquez sur le bouton **Valider** en regard de la zone de texte pour valider l'ID de compte.  
  
6.  Cliquez sur **OK** dans le message de confirmation.  
  
7.  Cliquez sur **Fermer** en bas de la page pour passer à la page principale du Client DQS.  
  
## <a name="next-task"></a>Tâche suivante  
 [Tâche 10 : Configuration d'un domaine pour utiliser un service de données de référence](../../2014/tutorials/task-10-configuring-composite-domain-to-use-reference-data-service.md)  
  
  
