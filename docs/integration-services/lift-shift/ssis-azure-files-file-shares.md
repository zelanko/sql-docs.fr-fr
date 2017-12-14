---
title: "Stocker et récupérer des fichiers sur des partages de fichiers locaux et dans Azure | Microsoft Docs"
description: "Cet article explique comment utiliser le système de fichiers et les partages de fichiers, aussi bien localement que dans Azure, avec SSIS"
ms.date: 11/10/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4980f39deea4d70817da3650dccbff7997ba83d
ms.sourcegitcommit: 06bb91d138a4d6395c7603a2d8f99c69a20642d3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2017
---
# <a name="store-and-retrieve-files-on-file-shares-on-premises-and-in-azure-with-ssis"></a>Stocker et récupérer des fichiers sur des partages de fichiers locaux et dans Azure avec SSIS
Cet article explique comment mettre à jour vos packages SSIS (SQL Server Integration Services) quand vous effectuez un « lift-and-shift » des packages qui utilisent des systèmes de fichiers locaux dans SSIS au sein d’Azure.

> [!IMPORTANT]
> Pour le moment, la base de données de catalogues SSIS (SSISDB) prend en charge uniquement un seul ensemble d’informations d’identification d’accès. Le runtime d’intégration Azure SSIS ne peut donc pas utiliser d’informations d’identification distinctes pour se connecter à plusieurs partages de fichiers locaux et partages Azure Files.

## <a name="store-temporary-files"></a>Stocker les fichiers temporaires
Si vous devez stocker et traiter des fichiers temporaires au cours d’une seule exécution de package, les packages peuvent utiliser le dossier temporaire `(.)/temp` ou `%TEMP%` de vos nœuds de runtime d’intégration Azure SSIS.

## <a name="store-files-across-multiple-package-executions"></a>Stocker des fichiers au cours de plusieurs exécutions de packages
Si vous devez stocker et traiter des fichiers permanents, et les conserver au cours de plusieurs exécutions de packages, vous pouvez utiliser des partages de fichiers locaux ou Azure Files

### <a name="use-on-premises-file-shares"></a>Utiliser des partages de fichiers locaux
Pour continuer à utiliser les **partages de fichiers locaux** quand vous faites un lift-and-shift des packages basés sur des systèmes de fichiers locaux dans SSIS au sein d’Azure, effectuez les actions suivantes :
1.  Transférez les fichiers des systèmes de fichiers locaux vers des partages de fichiers locaux.
2.  Joignez les partages de fichiers locaux à un réseau virtuel Azure (VNet).
3.  Joignez votre runtime d’intégration Azure SSIS au même réseau virtuel. Pour plus d’informations, consultez [Joindre un runtime d’intégration Azure SSIS à un réseau virtuel](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Connectez votre runtime d’intégration Azure SSIS aux partages de fichiers locaux dans le même réseau virtuel en configurant les informations d’identification d’accès qui utilisent l’authentification Windows. Pour plus d’informations, consultez [Se connecter à des sources de données locales et des partages de fichiers Azure avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).
5.  Mettez à jour les chemins de fichiers locaux de vos packages en fonction des chemins UNC qui pointent vers les partages de fichiers locaux. Par exemple, mettez à jour `C:\abc.txt` vers `\\<on-prem-server-name>\<share-name>\abc.txt`.

### <a name="use-azure-file-shares"></a>Utiliser les partages de fichiers Azure
Pour utiliser **Azure Files** quand vous faites un lift-and-shift des packages basés sur des systèmes de fichiers locaux dans SSIS au sein d’Azure, effectuez les actions suivantes :
1.  Transférez les fichiers des systèmes de fichiers locaux vers Azure Files. Pour plus d’informations, consultez [Azure Files](https://azure.microsoft.com/services/storage/files/).
2.  Connectez votre runtime d’intégration Azure SSIS à Azure Files en configurant les informations d’identification d’accès qui utilisent l’authentification Windows. Pour plus d’informations, consultez [Se connecter à des sources de données locales et des partages de fichiers Azure avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).
3.  Mettez à jour les chemins de fichiers locaux de vos packages en fonction des chemins UNC qui pointent vers Azure Files. Par exemple, mettez à jour `C:\abc.txt` vers `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`.
