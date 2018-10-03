---
title: 'Tâche 10 : Configuration d’un domaine pour utiliser le Service de données de référence | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4e4a8ef8c3b9d60040d6d9b5fcbff145a600cd88
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48167679"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>Tâche 10 : Configuration d'un domaine pour utiliser un service de données de référence
  Dans cette tâche, vous allez configurer le **Validation d’adresses** domaine composite à utiliser le **Melissa Data – contrôle d’adresse** service. Au moment de l'exécution, pendant l'activité de nettoyage, DQS passe les valeurs des domaines du domaine Validation d'adresses au service pour le nettoyage. Consultez [mappage de domaine/domaine Composite aux données de référence](http://msdn.microsoft.com/library/hh213030.aspx) pour plus d’informations.  
  
1.  Dans la page principale de **Client DQS**, cliquez sur **fournisseurs (gestion des domaines)** sous **base de connaissances récentes** pour lancer le **gestion des domaines**page.  
  
2.  Sélectionnez le **Validation d’adresses** domaine composite dans le **liste des domaines**.  
  
3.  Dans le volet droit, basculez vers le **les données de référence** onglet.  
  
     ![Onglet données de référence](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "onglet données de référence")  
  
4.  Cliquez sur **Parcourir** dans la barre d’outils.  
  
5.  Sur le **catalogue de fournisseurs de données de référence en ligne** boîte de dialogue, sélectionnez **case à cocher** regard **Melissa Data – contrôle d’adresse**.  
  
     ![Sélectionner Melissa Data – contrôle d’adresse](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "sélectionner Melissa Data – contrôle d’adresse")  
  
6.  Dans le volet droit, dans le **schéma** section, mappez **ligne d’adresse** domaine à la **adresse (M)** élément de schéma à l’aide de la liste déroulante.  
  
     ![Mapper un élément de schéma RDS au domaine](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "mapper l’élément de schéma RDS au domaine")  
  
7.  Cliquez sur **ajouter une entrée de schéma (+)** la barre d’outils pour créer une entrée dans la liste.  
  
     ![Ajouter le bouton de barre d’outils de l’entrée de schéma](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "ajouter le bouton de barre d’outils de l’entrée de schéma")  
  
8.  Mappez les domaines DQS suivants à l'aide des listes déroulantes, comme le montre l'image suivante.  
  
     ![Mapper les éléments de schéma RDS aux domaines](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "mapper les éléments de schéma RDS aux domaines")  
  
9. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 11 : Publication de la base de connaissances](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  
