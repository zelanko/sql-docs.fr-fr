---
title: 'Tâche 10 : configuration d’un domaine composite pour utiliser le service de données de référence | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 525e0286d8d82f501981c9e936caca581886b9b4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65481228"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>Tâche 10 : Configuration d’un domaine pour utiliser un service de données de référence
  Dans cette tâche, vous configurez le domaine composite **validation d’adresse** pour utiliser le service de **vérification d’adresse de données Melissa** . Au moment de l'exécution, pendant l'activité de nettoyage, DQS passe les valeurs des domaines du domaine Validation d'adresses au service pour le nettoyage. Pour plus d’informations, consultez mapper un domaine [/domaine composite à des données de référence](https://msdn.microsoft.com/library/hh213030.aspx) .  
  
1.  Dans la page principale du **client DQS**, cliquez sur **Suppliers (Domain Management)** sous **bases de connaissances récentes** pour lancer la page de **gestion des domaines** .  
  
2.  Sélectionnez le domaine composite **validation d’adresse** dans la **liste des domaines**.  
  
3.  Dans le volet droit, basculez vers l’onglet **données de référence** .  
  
     ![Onglet Données de référence](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "Onglet Données de référence")  
  
4.  Cliquez sur le bouton **Parcourir** dans la barre d’outils.  
  
5.  Dans la boîte de dialogue **catalogue des fournisseurs de données de référence en ligne** , **cochez la case en regard de** **Melissa Data-adresse Check**.  
  
     ![Sélectionner Melissa Data – Contrôle d'adresse](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "Sélectionner Melissa Data – Contrôle d'adresse")  
  
6.  Dans le volet droit, dans la section **schéma** , mappez **Address ligne** Domain à l’élément de schéma **address line (M)** à l’aide de la liste déroulante.  
  
     ![Mapper l'élément de schéma RDS au domaine](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "Mapper l'élément de schéma RDS au domaine")  
  
7.  Cliquez sur le bouton **Ajouter une entrée de schéma (+)** dans la barre d’outils pour créer une entrée dans la liste.  
  
     ![Bouton à la barre d'outils Ajouter une entrée de schéma](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "Bouton à la barre d'outils Ajouter une entrée de schéma")  
  
8.  Mappez les domaines DQS suivants à l'aide des listes déroulantes, comme le montre l'image suivante.  
  
     ![Mapper les éléments de schéma RDS aux domaines](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "Mapper les éléments de schéma RDS aux domaines")  
  
9. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 11 : Publication de la base de connaissances](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
