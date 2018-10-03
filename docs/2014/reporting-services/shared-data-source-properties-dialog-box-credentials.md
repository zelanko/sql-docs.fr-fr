---
title: Boîte de dialogue de propriétés de Source des données partagées, les informations d’identification | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shareddatasource.credentials.f1
ms.assetid: c08d1a5f-206b-4d53-ab1a-368b651ee5bb
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a6546a9b38c8f12e493ea9fa47741fa56c9fab79
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171075"
---
# <a name="shared-data-source-properties-dialog-box-credentials"></a>Boîte de dialogue Propriétés de la source de données partagée, Informations d'identification
  Sélectionnez **Informations d’identification** dans la boîte de dialogue **Propriétés de la source de données partagée** pour afficher et modifier les informations d’identification pour se connecter à une source de données partagée dans le rapport. Les informations d'identification que vous fournissez sont utilisées pour accéder à la source de données et pour mettre en cache une copie des données pour afficher un aperçu des rapports. Pour plus d’informations sur la mise en cache de l’aperçu des données, consultez [Aperçu des rapports](reports/previewing-reports.md). Pour plus d’informations sur les informations d’identification, consultez [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
## <a name="options"></a>Options  
 **Utiliser l’authentification Windows (sécurité intégrée)**  
 Sélectionnez cette option pour utiliser l’authentification Windows.  
  
 **Utiliser ce nom d’utilisateur et le mot de passe**  
 Sélectionnez cette option pour fournir un nom d'utilisateur et un mot de passe spécifiques. Pour les sources de données partagées : lorsque vous publiez un projet de serveur de rapports sur le serveur cible, le nom d'utilisateur et le mot de passe sont enregistrés sous la forme d'informations d'identification stockées pour la base de données. Si vous souhaitez utiliser le nom d’utilisateur et le mot de passe comme informations d’identification Windows, vous pouvez modifier les propriétés de la source de données partagée publiée sur le serveur cible. Pour plus d’informations, consultez [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).  
  
 **Nom d'utilisateur**  
 Tapez un nom d'utilisateur pour la connexion à la source de données.  
  
 **Mot de passe**  
 Tapez un mot de passe pour la connexion à la source de données.  
  
 **Invite pour les informations d’identification**  
 Sélectionnez cette option pour demander des informations d’identification pendant l’exécution du rapport.  
  
 **Entrez la chaîne d’invite**  
 Tapez une phrase pour indiquer à l'utilisateur de fournir des informations d'identification de connexion pour l'accès à la source de données.  
  
 **Aucune information d’identification**  
 Sélectionnez cette option pour ne pas demander d'informations d'identification pour la source de données. Cette option fonctionne uniquement si la source de données n’accepte pas les informations d’identification ou si vous transmettez les informations d’identification d’une autre façon.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions de données, Sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapport](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Propriétés de la source de données partagée, boîte de dialogue (Général)](../../2014/reporting-services/shared-data-source-properties-dialog-box-general.md)  
  
  
