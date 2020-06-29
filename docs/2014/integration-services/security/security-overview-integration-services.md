---
title: Vue d’ensemble de la sécurité (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- Integration Services, security
- security [Integration Services], about security
- passwords [Integration Services]
- packages [Integration Services], security
- SQL Server Integration Services, security
- SSIS, security
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 01aa0b88-d477-4581-9a3b-2efc3de2b133
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 597f6341c6542f9c53cb6f0243b94e77326a33d9
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422046"
---
# <a name="security-overview-integration-services"></a>Vue d'ensemble de la sécurité (Integration Services)
  La sécurité dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est constituée de plusieurs couches qui fournissent un environnement de sécurité complet et souple. Ces couches de sécurité incluent l’utilisation de signatures numériques, de propriétés de package, de rôles de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et d’autorisations de système d’exploitation. La plupart de ces fonctionnalités de sécurité se répartissent dans les catégories suivantes : identité et contrôle d'accès.  
  
## <a name="identity-features"></a>Fonctionnalités d'identité  
 En implémentant des fonctionnalités d'identité dans vos packages, vous pouvez atteindre l'objectif suivant :  
  
 **S'assurer d'ouvrir et d'exécuter uniquement des packages provenant de sources approuvées**.  
  
 Pour vous assurer d'ouvrir et d'exécuter uniquement des packages provenant de sources approuvées, vous devez tout d'abord identifier leur source. Pour ce faire, signez les packages avec des certificats. Puis, lorsque vous ouvrez ou exécutez le package, vous pouvez vérifier la présence et la validité des signatures numériques à l'aide d' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour plus d’informations, consultez [Identifier la source de packages à l’aide de signatures numériques](identify-the-source-of-packages-with-digital-signatures.md).  
  
## <a name="access-control-features"></a>Fonctionnalités de contrôle d'accès  
 En implémentant des fonctionnalités d'identité dans vos packages, vous pouvez atteindre l'objectif suivant :  
  
 **S'assurer que seuls les utilisateurs autorisés ouvrent et exécutent des packages**.  
  
 Pour vous assurer que seuls les utilisateurs autorisés ouvrent et exécutent des packages, vous devez contrôler l'accès aux informations suivantes.  
  
-   Contrôler l'accès au contenu des packages, en particulier les données sensibles.  
  
-   Contrôler l'accès aux packages et configurations de package stockés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Contrôler l'accès aux packages et aux fichiers connexes tels que les configurations, journaux et fichiers de point de contrôle stockés dans le système de fichiers.  
  
-   Contrôler l'accès au service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et aux informations sur les packages que le service affiche dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
### <a name="controlling-access-to-the-contents-of-packages"></a>Contrôle de l'accès au contenu des packages  
 Pour restreindre l’accès au contenu d’un package, vous pouvez chiffrer le package en définissant sa propriété ProtectionLevel. Vous pouvez définir cette propriété au niveau de protection requis par votre package. Par exemple, dans un environnement de développement en équipe, vous pouvez chiffrer un package à l'aide d'un mot de passe uniquement connu des membres de l'équipe qui travaillent sur celui-ci.  
  
 Lorsque vous définissez la propriété ProtectionLevel d’un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] détecte automatiquement les propriétés sensibles et les gère en fonction du niveau de protection spécifié. Par exemple, vous définissez la propriété ProtectionLevel d’un package à un niveau qui chiffre les informations sensibles à l’aide d’un mot de passe. Pour ce package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] chiffre automatiquement les valeurs de toutes les propriétés sensibles et n'affichera pas les données correspondantes sans que le mot de passe correct ne soit fourni.  
  
 En général, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] identifie des propriétés comme étant sensibles si elles contiennent des informations telles qu’un mot de passe ou une chaîne de connexion, ou si ces propriétés correspondent aux variables ou aux nœuds XML générés par la tâche. Le fait qu' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] considère une propriété comme sensible repose sur le fait que le développeur du composant [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , tel qu'un gestionnaire de connexions ou une tâche, l'a désignée comme sensible. Les utilisateurs ne peuvent pas ajouter de propriétés à, ni en supprimer de, la liste des propriétés considérées sensibles. Si vous écrivez des tâches personnalisées, des gestionnaires de connexions ou des composants de flux de données, vous pouvez spécifier les propriétés [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à considérer comme sensibles.  
  
 Pour plus d'informations, consultez [Access Control for Sensitive Data in Packages](access-control-for-sensitive-data-in-packages.md).  
  
### <a name="controlling-access-to-packages"></a>Contrôle de l'accès aux packages  
 Vous pouvez enregistrer des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans la base de données d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou dans le système de fichiers sous la forme de fichiers XML avec l'extension .dtsx. Pour plus d’informations, consultez [Enregistrer des packages](../save-packages.md).  
  
#### <a name="saving-packages-to-the-msdb-database"></a>Enregistrement de packages dans la base de données msdb  
 L'enregistrement des packages dans la base de données msdb permet d'assurer la sécurité au niveau du serveur, de la base de données et de la table. Dans la base de données msdb, les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sont stockés dans la table sysssispackages. Les packages étant enregistrés dans les tables sysssispackages et sysdtspackages de la base de données msdb, ils sont automatiquement sauvegardés lors de la sauvegarde de la base de données msdb.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Vous pouvez également protéger les packages stockés dans la base de données msdb en appliquant des rôles au niveau de la base de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut trois rôles fixes au niveau de la base de données : db_ssisadmin, db_ssisltduser et db_ssisoperator pour le contrôle de l’accès aux packages. Un rôle de lecture et d'écriture peut être associé à chaque package. Vous pouvez également définir des rôles personnalisés au niveau de la base de données pour les utiliser dans les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Les rôles ne peuvent être implémentés que sur les packages enregistrés dans la base de données msdb d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Rôles Integration Services &#40;Service SSIS&#41;](integration-services-roles-ssis-service.md).  
  
#### <a name="saving-packages-to-the-file-system"></a>Enregistrement de packages dans le système de fichiers  
 Si vous stockez des packages dans le système de fichiers plutôt que dans la base de données msdb, veillez à sécuriser les fichiers de package et les dossiers qui les contiennent.  
  
### <a name="controlling-access-to-files-used-by-packages"></a>Contrôle de l'accès aux fichiers utilisés par des packages  
 Les packages configurés pour utiliser des configurations, des points de contrôle et une journalisation génèrent des informations stockées en dehors du package. Ces informations peuvent être sensibles et doivent être protégées. Les fichiers de point de contrôle ne peuvent être enregistrés que dans le système de fichiers, mais les configurations et les journaux peuvent l'être dans le système de fichiers ou dans les tables d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les configurations et les journaux enregistrés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bénéficient de la sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mais les informations écrites dans le système de fichiers requièrent une sécurité supplémentaire.  
  
 Pour plus d’informations, consultez [accès aux fichiers utilisés par les packages](../access-to-files-used-by-packages.md).  
  
#### <a name="storing-package-configurations-securely"></a>Stockage sécurisé des configurations de package  
 Les configurations de package peuvent être enregistrées dans une table d'une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou dans le système de fichiers.  
  
 Les configurations peuvent être enregistrées dans n'importe qu'elle base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , et non pas uniquement dans la base de données msdb. Vous pouvez donc spécifier la base de données qui sert de référentiel de configurations de package. Vous pouvez également spécifier le nom de la table qui contiendra les configurations : [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée alors automatiquement la table avec la structure correcte. L'enregistrement des configurations dans une table permet d'assurer la sécurité au niveau du serveur, de la base de données et de la table. En outre, les configurations enregistrées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont automatiquement sauvegardées lors de la sauvegarde de la base de données.  
  
 Si vous stockez des configurations dans le système de fichiers plutôt que dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], veillez à sécuriser les dossiers qui contiennent les fichiers de configuration de package.  
  
 Pour plus d'informations sur les configurations, consultez [Package Configurations](../package-configurations.md).  
  
### <a name="controlling-access-to-the-integration-services-service"></a>Contrôle de l'accès au service Integration Services  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilise le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour établir la liste des packages stockés. Pour empêcher tout utilisateur non autorisé de consulter des informations sur les packages stockées sur des ordinateurs locaux et distants, et par conséquent d'accéder à des informations privées, restreignez l'accès aux ordinateurs qui exécutent le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Pour plus d’informations, consultez [Accéder au service Integration Services](../access-to-the-integration-services-service.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 La liste suivante contient des liens vers les rubriques qui indiquent comment effectuer une tâche particulière relative à la sécurité.  
  
-   [Créer un rôle défini par l'utilisateur](../create-a-user-defined-role.md)  
  
-   [Affecter un rôle de lecture et d'écriture à un package](../assign-a-reader-and-writer-role-to-a-package.md)  
  
-   [Implémenter une stratégie de signature en définissant une valeur du Registre](../implement-a-signing-policy-by-setting-a-registry-value.md)  
  
-   [Signer un package à l'aide d'un certificat numérique](../sign-a-package-by-using-a-digital-certificate.md)  
  
-   [Définir ou modifier le niveau de protection des packages](../set-or-change-the-protection-level-of-packages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
