---
title: Sélectionner la source de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6dab6158ba2d0854868bf60f2a73efce594b2cc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101438"
---
# <a name="select-the-data-source"></a>Sélectionner la source de données
  Utilisez cette page de l'Assistant Rapport pour définir une source de données pour le rapport.  
  
## <a name="options"></a>Options  
 **Source de données partagée**  
 Sélectionnez **Source de données partagée** pour utiliser une source de données partagée prédéfinie qui a déjà les informations de connexion à la source de données que vous souhaitez utiliser. Cette liste contient toutes les sources de données partagées incluses dans le projet.  
  
 **Nouvelle source de données**  
 Sélectionnez **Nouvelle source de données** pour définir une nouvelle source de données. Les informations sur la source de données seront utilisées uniquement avec le rapport actuel.  
  
 **Nom**  
 Tapez un nom pour la connexion à la source de données. Ce nom de source de données doit être unique dans le rapport.  
  
 **Type**  
 Sélectionnez le type de source de données que vous utilisez (par exemple, si vous utilisez une [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] base de données [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], choisissez).  
  
 **Chaîne de connexion**  
 Tapez une chaîne de connexion pour la source de données. Pour plus d’informations sur les chaînes de connexion, consultez [connexions de données, sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 Cliquez sur **Modifier** pour spécifier le serveur de source de données dans la boîte de dialogue **Propriétés de connexion** . Vous pouvez spécifier une source de données locale ou distante.  
  
 Cliquez sur **Informations d'identification** pour fournir les informations d'identification à la base de données. Au minimum, les informations d'identification spécifiées doivent être suffisantes pour que vous puissiez vous connecter à la source de données à des fins de génération de rapports. Lorsque le rapport est déployé sur un serveur de rapports, les informations d'identification à la base de données doivent tenir compte de tous les utilisateurs du rapport. Par exemple, si vous souhaitez que tous les utilisateurs du rapport se connectent à la source de données en utilisant leurs informations d’identification, choisissez **Utiliser l’authentification Windows (sécurité intégrée)**. Les informations d'identification que vous spécifiez doivent être valides pour la source de données ; par conséquent, si vous choisissez l'authentification Windows, assurez-vous que la source de données accepte les connexions à partir des comptes de tous les utilisateurs qui exécuteront le rapport. Les informations d'identification à la base de données peuvent être gérées indépendamment du rapport. Pour plus d’informations, consultez [Gérer les sources de données de rapports](report-data/manage-report-data-sources.md).  
  
 **Transformer en une source de données partagée**  
 Sélectionnez cette option pour stocker la source de données dans le projet en tant que source de données partagée et non dans le rapport. De cette façon, vous pouvez l'utiliser comme source de données pour d'autres rapports dans le projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions de données ou sources de données incorporées et partagées &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Spécifier les informations d’identification et de connexion pour les sources de données de rapport](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Reporting Services le serveur de rapports](../../2014/reporting-services/reporting-services-report-server.md)   
 [Fichier de configuration RSReportDesigner](report-server/rsreportdesigner-configuration-file.md)   
 [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Aide de l'Assistant Rapport](../../2014/reporting-services/report-wizard-help.md)  
  
  
