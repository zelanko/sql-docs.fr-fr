---
title: Informations d’identification (Générateur de rapports), boîte de dialogue Propriétés de Source de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10017"
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 18c950015de84ac6b4204e657dfd52f894b6bced
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48207429"
---
# <a name="data-source-properties-dialog-box-credentials-report-builder"></a>Boîte de dialogue Propriétés de la source de données, Informations d'identification (Générateur de rapports)
  Sélectionnez **Informations d’identification** dans la boîte de dialogue **Propriétés de la source de données** pour afficher et modifier les informations d’identification pour se connecter à une source de données incorporée dans le rapport. Les informations d'identification que vous fournissez permettent d'accéder à la source de données pour afficher un aperçu des rapports. Pour plus d’informations sur les informations d’identification, consultez [Spécifier des informations d’identification dans le Générateur de rapports](../../2014/reporting-services/specify-credentials-in-report-builder.md).  
  
## <a name="options"></a>Options  
 **Utiliser l’authentification Windows (sécurité intégrée)**  
 Sélectionnez cette option pour utiliser l’authentification Windows.  
  
 **Utiliser ce nom d’utilisateur et le mot de passe**  
 Sélectionnez cette option pour fournir un nom d'utilisateur et un mot de passe spécifiques. Pour les sources de données incorporées : lorsque vous publiez un projet de serveur de rapports sur le serveur cible, le nom d'utilisateur et le mot de passe sont enregistrés sous la forme d'informations d'identification stockées pour la base de données. Si vous voulez utiliser le nom d'utilisateur et le mot de passe comme informations d'identification Windows, vous pouvez modifier les propriétés de la source de données partagée publiée sur le serveur cible. Pour plus d’informations, consultez [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) dans la [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][documentation en ligne](http://go.microsoft.com/fwlink/?linkid=121312) de .  
  
 **Nom d'utilisateur**  
 Tapez un nom d’utilisateur pour la connexion à la source de données.  
  
 **Mot de passe**  
 Tapez un mot de passe pour la connexion à la source de données.  
  
 **Invite pour les informations d’identification**  
 Sélectionnez cette option pour demander des informations d'identification lors de l'exécution du rapport.  
  
 **Entrez la chaîne d’invite**  
 Tapez une phrase pour indiquer à l'utilisateur de fournir des informations d'identification de connexion pour l'accès à la source de données.  
  
 **Aucune information d’identification**  
 Sélectionnez cette option pour ne pas demander d'informations d'identification pour la source de données. Cette option fonctionne uniquement si la source de données n’accepte pas les informations d’identification ou si vous transmettez les informations d’identification d’une autre façon.  
  
 Dans certaines extensions de données, le compte d'exécution sans assistance doit être configuré sur le serveur de rapports.  
  
 Pour plus d’informations, consultez la rubrique relative au type de source de données correspondant dans [Ajouter des données à partir de sources de données externes &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) et [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]dans la [documentation en ligne](http://go.microsoft.com/fwlink/?linkid=121312) de .  
  
## <a name="see-also"></a>Voir aussi  
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Boîte de dialogue Propriétés de la source de données, Général &#40;Générateur de rapports&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md)   
 [Ajouter et vérifier une connexion de données ou d’une Source de données &#40;Générateur de rapports et SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
