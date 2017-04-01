---
title: "Sp&#233;cification de param&#232;tres de configuration pour le d&#233;ploiement de solutions | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assistant Déploiement d’Analysis Services, paramètres de configuration"
  - "fichiers d'entrée [Analysis Services]"
  - "options de configuration [Analysis Services]"
  - "déploiements Analysis Services, paramètres de configuration"
  - "déploiement [Analysis Services], paramètres de configuration"
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Sp&#233;cification de param&#232;tres de configuration pour le d&#233;ploiement de solutions
  L’Assistant Déploiement d’[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lit les options de déploiement de partitions et de rôles que vous utilisez dans le script de déploiement dans le fichier \<*nom du projet*>.configsettings. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée ce fichier lorsque vous générez le projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise les paramètres de configuration du projet actif pour créer le fichier \<*nom du projet*>.configsettings.  
  
## Examen des paramètres de configuration pour le déploiement  
 Les paramètres de configuration stockés dans le fichier \<*nom du projet*>.configsettings sont les suivants :  
  
-   **Chaînes de connexion à la source de données** Il s'agit des chaînes de connexion pour chaque source de données, basées sur les valeurs spécifiées dans le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . L'ID et le mot de passe utilisateur sont systématiquement supprimés de la chaîne de connexion avant que le reste de la chaîne ne soit stocké dans ce fichier. Cependant, si l'Assistant Déploiement déploie directement vers une instance Analysis Services, vous pouvez ajouter les informations d'ID et de mot de passe utilisateur appropriées dans l'Assistant pour permettre le traitement correct de la base de données de déploiement. Ces informations de connexion ne seront pas stockées dans le script de déploiement proprement dit, si un script est enregistré par l'Assistant Déploiement.  
  
-   **Comptes d'emprunt d'identité** Ce paramètre spécifie le nom d'utilisateur que [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise pour exécuter les instructions dans chaque source de données. Si aucun compte d'emprunt d'identité n'est spécifié, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise son compte d'ouverture de session pour exécuter les instructions. Si le compte d'ouverture de session [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] reçoit des autorisations directement dans la source de données, tous les administrateurs de base de données de toutes les bases de données de l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ont accès à la source de données à travers le compte d'ouverture de session. Si un mot de passe et un compte d'utilisateur sont spécifiés, ces informations sont systématiquement supprimées avant que les informations d'emprunt d'identité ne soient stockées dans ce fichier. Cependant, si l'Assistant Déploiement déploie directement vers une instance Analysis Services, vous pouvez ajouter les informations d'ID et de mot de passe utilisateur appropriées dans l'Assistant pour permettre le traitement correct de la base de données de déploiement. Ces informations d'emprunt d'identité ne sont pas stockées dans le script de déploiement proprement dit, si un script est enregistré par l'Assistant Déploiement.  
  
-   **Fichiers journaux d'erreurs de clé** Ce paramètre spécifie le nom de fichier et le chemin d'accès du fichier journal d'erreurs de clé pour chaque cube, groupe de mesures, partition et dimension de la base de données.  
  
-   **Emplacements de stockage** Ce paramètre spécifie l'emplacement de stockage pour chaque cube, groupe de mesures et partition de la base de données. Si aucune valeur n'est fournie pour un objet, l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise l'emplacement par défaut pour l'objet. Par exemple, les partitions utilisent l'emplacement pour le groupe de mesures, les groupes de mesures utilisent l'emplacement pour le cube et les cubes utilisent l'emplacement par défaut pour les objets sur l'instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . L'emplacement de stockage peut être un chemin d'accès local ou UNC (Universal Naming Convention).  
  
-   **Report Server** Ce paramètre spécifie le serveur de rapports et l'emplacement du dossier pour chaque action de rapport définie dans chaque cube de la base de données.  
  
## Modification des paramètres de configuration pour le déploiement  
 Dans certains cas, il peut s’avérer nécessaire de déployer un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] avec des paramètres de configuration différents de ceux stockés dans le fichier \<*nom du projet*>.configsettings. Par exemple, vous pouvez modifier la chaîne de connexion à une ou plusieurs sources de données, ou spécifier des emplacements de stockage pour des partitions ou des groupes de mesures spécifiques.  
  
 Pour modifier le déploiement des partitions et des rôles dans un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous devez modifier ces informations dans le fichier \<*nom du projet*>.configsettings, conformément à la procédure décrite ci-dessous. Vous ne pouvez pas modifier les paramètres de partitions et de rôles au sein du projet, car la boîte de dialogue **Pages de propriétés** *\<nom du projet>* de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ne présente pas ces options.  
  
> [!NOTE]  
>  Les paramètres de configuration peuvent s'appliquer à tous les objets ou uniquement aux objets nouvellement créés. Appliquez les paramètres de configuration uniquement aux objets nouvellement créés lorsque vous ajoutez des objets supplémentaires à une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déployée antérieurement et que vous ne souhaitez pas recouvrir des objets existants. Pour spécifier si les paramètres de configuration s’appliquent à tous les objets ou seulement aux nouveaux, définissez cette option dans le fichier \<*nom du projet*>.deploymentoptions. Pour plus d’informations, consultez [Spécification des options de déploiement de partitions et de rôles](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md).  
  
#### Pour modifier des paramètres de configuration après la génération des fichiers d'entrée  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode interactif et, dans la page **Paramètres de configuration** , spécifiez les paramètres de configuration pour les objets déployés.  
  
     —ou—  
  
-   Exécutez l'Assistant Déploiement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à l'invite de commandes en mode fichier de réponses. Pour plus d'informations sur le mode fichier de réponses, consultez [Running the Analysis Services Deployment Wizard](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     —ou—  
  
-   Modifiez le fichier \<*nom du projet*>.configsettings à l’aide d’un éditeur de texte.  
  
## Voir aussi  
 [Spécification de la cible d'installation](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)   
 [Spécification des options de déploiement de partitions et de rôles](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)   
 [Spécification d'options de traitement](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  