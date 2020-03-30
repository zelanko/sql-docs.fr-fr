---
title: Vue d’ensemble de SQL Server Integration Services DevOps | Microsoft Docs
description: Découvrez comment créer le CICD dans SSIS avec SSIS DevOps Tools.
ms.date: 12/06/2019
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6a1f903d0be82d6f5057af68dce80bda1e48238a
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "78225922"
---
# <a name="sql-server-integration-services-ssis-devops-tools-preview"></a>SQL Server Integration Services (SSIS) DevOps Tools (préversion)

L’extension [SSIS DevOps Tools](https://marketplace.visualstudio.com/items?itemName=SSIS.ssis-devops-tools) est disponible sur la Place de Marché **Azure DevOps**.

Si vous n’avez pas d’organisation **Azure DevOps**, vous devez tout d’abord vous inscrire à [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started/pipelines-sign-up?view=azure-devops), puis ajouter l’extension **SSIS DevOps Tools** en suivant [ces étapes](https://docs.microsoft.com/azure/devops/marketplace/overview?view=azure-devops&tabs=browser#add-an-extension).

**SSIS DevOps Tools** inclut la tâche de **génération SSIS** et la tâche de fin de **déploiement SSIS**.

- La tâche de **génération SSIS** prend en charge la génération de fichiers dtproj dans un modèle de déploiement de projet ou de package.

- La tâche de **déploiement SSIS** prend en charge le déploiement d’un ou plusieurs fichiers ispac dans un catalogue SSIS local et un runtime d’intégration Azure-SSIS ou de fichiers SSISDeploymentManifest et des fichiers associés dans un partage de fichiers Azure ou local.

## <a name="ssis-build-task"></a>Tâche de génération SSIS

![tâche de génération](media/ssis-build-task.png)

### <a name="properties"></a>Propriétés

#### <a name="project-path"></a>Chemin du projet

Chemin du fichier ou dossier de projet à générer. Si un chemin de dossier est spécifié, la tâche de génération SSIS recherchera tous les fichiers dtproj de manière récursive dans ce dossier et les générera tous.

Le chemin du projet ne peut pas être *vide*, défini comme **.** pour effectuer une génération à partir du dossier racine du référentiel.

#### <a name="project-configuration"></a>Configuration du projet

Nom de la configuration de projet à utiliser pour la génération. S’il n’est pas spécifié, il s’agit, par défaut, de la première configuration de projet définie dans chaque fichier dtproj.

#### <a name="output-path"></a>Chemin de sortie

Chemin d’un dossier distinct où seront enregistrés les résultats de la génération. Ceux-ci peuvent être publiés comme artefact de build à l’aide de la [tâche de publication d’artefacts de build](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/publish-build-artifacts?view=azure-devops).

### <a name="limitations-and-known-issues"></a>Limitations et problèmes connus

- La tâche de génération SSIS s’appuie sur Visual Studio et le concepteur SSIS (obligatoire avec les agents de build). Ainsi, pour exécuter la tâche de génération SSIS dans le pipeline, vous devez choisir **vs2017-win2016** pour les agents hébergés par Microsoft ou installer Visual Studio et le concepteur SSIS (VS2017 + SSDT2017 ou VS2019 + extension de projets SSIS) sur les agents autohébergés.

- Pour générer des projets SSIS à l’aide de composants prêts à l’emploi (quels qu’ils soient, y compris le Feature Pack SSIS Azure ou d’autres composants tiers), veillez à ce que ces composants soient installés sur l’ordinateur sur lequel s’exécute l’agent de pipeline.  Pour l’agent hébergé par Microsoft, l’utilisateur peut ajouter une [tâche de script PowerShell](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/powershell?view=azure-devops) ou une [tâche de script de ligne de commande](https://docs.microsoft.com/azure/devops/pipelines/tasks/utility/command-line?view=azure-devops) pour télécharger et installer les composants avant l’exécution de la tâche de génération SSIS. Voici l’exemple de script PowerShell permettant d’installer Azure Feature Pack : 

```powershell
wget -Uri https://download.microsoft.com/download/E/E/0/EE0CB6A0-4105-466D-A7CA-5E39FA9AB128/SsisAzureFeaturePack_2017_x86.msi -OutFile AFP.msi

start -Wait -FilePath msiexec -Args "/i AFP.msi /quiet /l* log.txt"

cat log.txt
```

- Les niveaux de protection **EncryptSensitiveWithPassword** et **EncryptAllWithPassword** ne sont pas pris en charge par la tâche de génération SSIS. Veillez à ce qu’aucun des projets SSIS du code base n’utilise ces deux niveaux de protection. Sinon, la tâche de génération SSIS se bloquera et dépassera le délai d’attente pendant l’exécution.

- **ConnectByProxy** est une nouvelle propriété ajoutée récemment à SSDT. SSDT installé sur l’agent hébergé par Microsoft n’est pas mis à jour. Par conséquent, utilisez plutôt l’agent autohébergé.

## <a name="ssis-deploy-task"></a>Tâche de déploiement SSIS

![tâche de déploiement](media/ssis-deploy-task.png)

### <a name="properties"></a>Propriétés

#### <a name="source-path"></a>Chemin source

Chemin des fichiers ISPAC ou SSISDeploymentManifest sources que vous souhaitez déployer. Il peut s’agir d’un chemin de dossier ou de fichier.

#### <a name="destination-type"></a>Type de destination

Type de la destination. Actuellement, la tâche de déploiement SSIS prend en charge deux types :

- *Système de fichiers* : les fichiers SSISDeploymentManifest et les fichiers associés sont déployés dans un système de fichiers spécifié. Les partages de fichiers locaux et Azure sont pris en charge.
- *SSISDB* : les fichiers ISPAC sont déployés dans un catalogue SSIS spécifié, qui peut être hébergé sur un serveur SQL Server local ou un runtime d’intégration Azure-SSIS.

#### <a name="destination-server"></a>Serveur de destination

Nom du serveur SQL Server de destination. Il peut s’agir du nom d’une instance SQL Server locale, d’une instance Azure SQL Database ou d’une instance managée Azure SQL Database. Cette propriété est visible uniquement si le type de destination est SSISDB.

#### <a name="destination-path"></a>Chemin de destination

Chemin du dossier de destination dans lequel le fichier source sera déployé. Par exemple :

- /SSISDB/\<folderName\>
- \\\\\<machineName\>\\\<shareFolderName\>\\\<optionalSubfolderName\>

La tâche de déploiement SSIS crée le dossier et le sous-dossier s’ils n’existent pas.

#### <a name="authentication-type"></a>Type d'authentification

Type d’authentification utilisé pour l’accès au serveur de destination spécifié. Cette propriété est visible uniquement si le type de destination est SSISDB. En général, la tâche de déploiement SSIS prend en charge quatre types d’authentification :

- Authentification Windows
- l’authentification SQL Server
- Active Directory - Authentification par mot de passe
- Active Directory - Authentification intégrée

Cependant, la prise en charge d’un type d’authentification spécifique dépend du type de serveur de destination et du type d’agent. Reportez-vous au tableau de prise en charge détaillé ci-dessous.

| |Agent hébergé par Microsoft|Agent autohébergé|
|---------|---------|---------|
|Serveur SQL Server local ou machine virtuelle |N/A|Authentification Windows|
|Azure SQL|l’authentification SQL Server <br> Active Directory - Authentification par mot de passe|l’authentification SQL Server <br> Active Directory - Authentification par mot de passe <br> Active Directory - Authentification intégrée|

#### <a name="domain-name"></a>Nom de domaine

Nom de domaine utilisé pour l’accès au système de fichiers spécifié. Cette propriété est visible uniquement si le type de destination est Système de fichiers.
Vous pouvez la laisser vide si le compte d’utilisateur utilisé pour l’exécution de l’agent autohébergé dispose d’un accès en lecture/écriture au chemin de destination spécifié.

#### <a name="username"></a>Nom d’utilisateur

Nom d’utilisateur utilisé pour l’accès à la base de données SSISDB ou au système de fichiers spécifié. Cette propriété est visible si le type de destination est Système de fichiers ou si le type d’authentification est Authentification SQL Server ou Active Directory - Authentification par mot de passe.
Vous pouvez la laisser vide si le type de destination est Système de fichiers et si le compte d’utilisateur utilisé pour l’exécution de l’agent autohébergé dispose d’un accès en lecture/écriture au chemin de destination spécifié.

#### <a name="password"></a>Mot de passe

Mot de passe utilisé pour l’accès à la base de données SSISDB ou au système de fichiers spécifié. Cette propriété est visible si le type de destination est Système de fichiers ou si le type d’authentification est Authentification SQL Server ou Active Directory - Authentification par mot de passe.
Vous pouvez la laisser vide si le type de destination est Système de fichiers et si le compte d’utilisateur utilisé pour l’exécution de l’agent autohébergé dispose d’un accès en lecture/écriture au chemin de destination spécifié.

#### <a name="overwrite-existing-projects-or-ssisdeploymentmanifest-files-of-the-same-names"></a>Remplacer les projets ou fichiers SSISDeploymentManifest existants portant le même nom

Indique si les projets ou fichiers SSISDeploymentManifest existants portant le même nom doivent être remplacés. Si vous sélectionnez « Non », la tâche de déploiement SSIS ignorera le déploiement de ces projets ou fichiers.

#### <a name="continue-deployment-when-error-occurs"></a>Continuer le déploiement si une erreur se produit

Indique si le déploiement des projets ou fichiers restants doit continuer quand une erreur se produit. Si vous sélectionnez « Non », la tâche de déploiement SSIS s’arrêtera immédiatement si une erreur se produit.

### <a name="limitations-and-known-issues"></a>Limitations et problèmes connus

Actuellement, la tâche de déploiement SSIS ne prend pas en charge les scénarios suivants :

- Configuration de l’environnement dans le catalogue SSIS
- Déploiement de fichiers ISPAC sur Azure SQL Server ou Azure SQL Managed Instance, qui autorise uniquement l’authentification multifacteur (MFA)
- Déploiement de packages dans MSDB ou le magasin de packages SSIS

## <a name="release-notes"></a>Notes de publication

### <a name="version-013-preview"></a>Version 0.1.3 - préversion

Date de publication : 19 janvier 2020

- Correction d’un problème qui empêchait le déploiement d’ISPAC si son nom de fichier d’origine était modifié.

### <a name="version-012-preview"></a>Version 0.1.2 - préversion

Date de publication : 13 janvier 2020

- Ajout d’informations plus détaillées sur les exceptions dans le journal des tâches SSIS Deploy lorsque le type de destination est SSISDB.
- Correction de l’exemple de chemin de destination dans le texte d’aide du chemin de destination de la propriété de la tâche SSIS Deploy.

### <a name="version-011-preview"></a>Version 0.1.1 - préversion

Date de publication : 6 janvier 2020

- Ajout d’une restriction pour la version minimale requise de l’agent. Actuellement, la version minimale de l’agent de ce produit est 2.144.0.
- Correction de texte d’affichage incorrect pour la tâche SSIS Deploy.
- Amélioration de certains messages d’erreur.

### <a name="version-010-preview"></a>Version 0.1.0 - préversion

Date de publication : 5 décembre 2019

Version initiale de SSIS DevOps Tools. Il s’agit d’une version préliminaire.

## <a name="next-steps"></a>Étapes suivantes

- Obtenir l’[extension SSIS DevOps](https://marketplace.visualstudio.com/items?itemName=SSIS.ssis-devops-tools)
