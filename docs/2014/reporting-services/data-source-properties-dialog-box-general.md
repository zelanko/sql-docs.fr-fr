---
title: Général, boîte de dialogue Propriétés de Source de données | Documents Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.general.f1
- "10120"
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
caps.latest.revision: 35
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 823604c6116c78f4313d5f1e328d98d7ed35f950
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151859"
---
# <a name="data-source-properties-dialog-box-general"></a>Boîte de dialogue Propriétés de la source de données, Général
  Sélectionnez **Général** dans la boîte de dialogue **Propriétés de la source de données** pour afficher et modifier les informations de connexion d'une source de données du rapport.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de la source de données. Ce nom de source de données doit être unique dans le rapport. Par défaut, un nom général, tel que DataSource1 ou DataSource2, est assigné à la source de données.  
  
 **Connexion incorporée**  
 Sélectionnez cette option lorsque vous ne souhaitez pas utiliser une source de données partagée.  
  
 **Type**  
 Sélectionnez une extension pour le traitement des données. La liste affiche toutes les extensions inscrites.  
  
 **Chaîne de connexion**  
 Entrez une chaîne de connexion pour la source de données. Cliquez sur **Modifier** pour créer la chaîne de connexion à l'aide de la boîte de dialogue **Propriétés de connexion** . Cliquez sur le bouton **Expressions** (*fx*) pour modifier l’expression.  
  
 **Utiliser la référence de source de données partagée**  
 Sélectionnez cette option pour créer un lien vers une source de données partagée. Sélectionnez une source de données partagée dans la liste déroulante. Pour modifier la source de données sélectionnée, cliquez sur **Modifier**. Si l'option **Utiliser une référence de source de données partagée** est sélectionnée, les options **Type** et **Chaîne de connexion** sont désactivées.  
  
 **Utiliser une transaction unique lors du traitement des requêtes**  
 Sélectionnez cette option pour indiquer que les datasets qui utilisent cette source de données sont exécutés dans une transaction unique sur la base de données. Pour inclure des transactions pour les sous-rapports qui utilisent la même source de données, définissez **MergeTransactions** à **True** dans la section **Autre** du volet **Propriétés** du sous-rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des données à un rapport &#40;rapport Générateur et SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Créer une Source de données incorporée ou partagée &#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md)   
 [Connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Boîte de dialogue Propriétés données Source, informations d’identification](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)  
  
  