---
title: Général (Générateur de rapports), boîte de dialogue Propriétés de Source de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10018"
ms.assetid: b956f43a-8426-4679-acc1-00f405d5ff5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bedf016dce02928bbd47dbfce60943ec667a824
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66109469"
---
# <a name="data-source-properties-dialog-box-general-report-builder"></a>Boîte de dialogue Propriétés de la source de données, Général (Générateur de rapports)
  Sélectionnez **Général** dans la boîte de dialogue **Propriétés de la source de données** pour sélectionner une source de données partagée à partir d'un serveur de rapports, ou pour créer ou modifier les informations de connexion d'une source de données incorporée au rapport.  
  
 Le type d'informations d'identification utilisé pour se connecter à une source de données est spécifié dans les propriétés de la source de données. Lorsque vous ouvrez un rapport à partir du serveur de rapports, les informations d'identification d'exécution, spécifiées dans les propriétés de la source de données, peuvent ne pas être appropriées pour des tâches de conception telles que la création de requêtes et l'aperçu des rapports. Par exemple, la source de données peut utiliser des informations d'identification Windows autres que les vôtres ou un nom d'utilisateur et un mot de passe inconnus de vous.  
  
 Le Générateur de rapports ouvre la boîte de dialogue **Entrez les informations d'identification pour la source de données** lorsqu'il ne peut pas se connecter à la source de données à l'aide des informations d'identification fournies dans les propriétés de cette source. Ceci se produit en général dans les cas suivants :  
  
-   La source de données est configurée de manière à inviter les utilisateurs à fournir des informations d'identification.  
  
-   La source de données est configurée de manière à utiliser les informations d'identification stockées.  Pour limiter les menaces de sécurité potentielles, le Générateur de rapports est conçu de manière à ne pas récupérer les informations d'identification stockées sur le serveur.  
  
 Vous pouvez utiliser la boîte de dialogue **Entrez les informations d'identification pour la source de données** pour modifier les informations d'identification utilisées par le Générateur de rapports au moment de la conception pour se connecter à la source de données comme étant l'utilisateur Windows actuel, ou pour fournir un nom d'utilisateur et un mot de passe. Si vous fournissez un nom d'utilisateur et un mot de passe, vous pouvez indiquer s'ils sont utilisés comme informations d'identification Windows.  
  
> [!NOTE]  
>  Bien que les concepteurs de requêtes vous permettent de spécifier d'autres types d'informations d'identification pour les informations d'identification au moment de la conception, l'aperçu du rapport vous permet seulement d'entrer le nom d'utilisateur et le mot de passe pour les options d'informations d'identification existantes spécifiées dans la source de données.  
  
 Lorsque vous cliquez sur **Tester la connexion**, la connexion à la source de données est testée à l'aide des informations d'identification spécifiées sur la page d'informations d'identification des propriétés de la source de données. Vous pouvez tester la connexion à des sources de données incorporées et partagées.  
  
 Si les informations d'identification spécifiées sont incomplètes (par exemple, si un mot de passe est obligatoire), le Générateur de rapports vous invite une nouvelle fois à saisir les informations d'identification d'exécution lorsqu'il doit se connecter à la source de données. Les informations d'identification à la conception sont stockées et il ne vous est plus demandé de les indiquer.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de la source de données. Ce nom de source de données doit être unique dans le rapport. Par défaut, un nom général, tel que DataSource1 ou DataSource2, est assigné à la source de données.  
  
 **Utiliser une connexion partagée**  
 Sélectionnez cette option pour accéder à une source de données partagée qui a été publiée sur un serveur de rapports.  
  
 Après avoir sélectionné une source de données à partir d'un serveur de rapports, le Générateur de rapports conserve une connexion à ce serveur de rapports.  
  
 **Utiliser une connexion incorporée dans mon rapport**  
 Sélectionnez cette option pour créer une source de données qui est utilisée uniquement par ce rapport.  
  
 **Type**  
 Sélectionnez une extension pour le traitement des données. La liste affiche toutes les extensions inscrites.  
  
 **Chaîne de connexion**  
 Entrez une chaîne de connexion pour la source de données. Cliquez sur **Générer** pour générer la chaîne de connexion à l'aide de la boîte de dialogue **Propriétés de connexion** . Cliquez sur le bouton **Expressions** (*fx*) pour modifier l’expression.  
  
 **Utiliser une transaction unique lors du traitement des requêtes**  
 Sélectionnez cette option pour indiquer que les datasets qui utilisent cette source de données sont exécutés dans une transaction unique sur la base de données. Pour inclure des transactions pour les sous-rapports qui utilisent la même source de données, sélectionnez le sous-rapport et, dans le volet Propriétés, affectez à **MergeTransactions** la valeur **True**.  
  
 **Tester la connexion**  
 Cliquez pour vérifier le fonctionnement de la connexion à la source de données à l'aide des informations d'identification spécifiées. Si la connexion ne peut pas être établie, vérifiez vos informations d'identification et la disponibilité du serveur. Vous pouvez tester la connexion de la source de données à des sources de données incorporées et partagées.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Ajouter et vérifier une connexion de données ou d’une Source de données &#40;Générateur de rapports et SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)   
 [Informations d’identification, boîte de dialogue Propriétés de Source de données &#40;Générateur de rapports&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
