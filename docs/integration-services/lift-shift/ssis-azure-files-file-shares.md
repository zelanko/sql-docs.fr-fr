---
title: Ouvrir et enregistrer des fichiers avec des packages SSIS déployés dans Azure | Microsoft Docs
description: Découvrez comment ouvrir et enregistrer des fichiers localement et dans Azure quand effectuez un lift-and-shift de packages SSIS qui utilisent des systèmes de fichiers locaux dans SSIS dans Azure.
ms.date: 11/27/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c4f9d5e91db382d59dc156ed919c1af06cc56b77
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35410471"
---
# <a name="open-and-save-files-on-premises-and-in-azure-with-ssis-packages-deployed-in-azure"></a>Ouvrir et enregistrer des fichiers localement et dans Azure avec des packages SSIS déployés dans Azure

Cet article explique ouvrir et enregistrer des fichiers localement et dans Azure quand effectuez un lift-and-shift de packages SSIS qui utilisent des systèmes de fichiers locaux dans SSIS dans Azure.

> [!IMPORTANT]
> Actuellement, le catalogue SSIS (SSISDB) ne prend en charge qu’un seul ensemble d’informations d’identification d’accès. Vous ne pouvez donc pas utiliser différents ensembles d’informations d’identification pour vous connecter à plusieurs partages de fichiers locaux et partages Azure Files.

## <a name="save-temporary-files"></a>Enregistrer des fichiers temporaires
Si vous devez stocker et traiter des fichiers temporaires au cours d’une même exécution d’un package, les packages peuvent utiliser le répertoire de travail actuel (`.`) ou le répertoire temporaire (`%TEMP%`) de vos nœuds Azure SSIS Integration Runtime.

## <a name="use-on-premises-file-shares"></a>Utiliser des partages de fichiers locaux
Pour continuer à utiliser les **partages de fichiers locaux** quand vous faites un lift-and-shift des packages basés sur des systèmes de fichiers locaux dans SSIS au sein d’Azure, effectuez les actions suivantes :
1.  Transférez les fichiers des systèmes de fichiers locaux vers des partages de fichiers locaux.
2.  Joignez les partages de fichiers locaux à un réseau virtuel Azure.
3.  Joignez votre runtime d’intégration Azure-SSIS au même réseau virtuel. Pour plus d’informations, consultez [Joindre un runtime d’intégration Azure SSIS à un réseau virtuel](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Connectez votre runtime d’intégration Azure-SSIS aux partages de fichiers locaux dans le même réseau virtuel en configurant des informations d’identification d’accès qui utilisent l’authentification Windows. Pour plus d’informations, consultez [Se connecter à des données et des partages de fichiers avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).
5.  Mettez à jour les chemins de fichiers locaux de vos packages en fonction des chemins UNC qui pointent vers les partages de fichiers locaux. Par exemple, mettez à jour `C:\abc.txt` vers `\\<on-prem-server-name>\<share-name>\abc.txt`.

## <a name="use-azure-file-shares"></a>Utiliser les partages de fichiers Azure
Pour utiliser **Azure Files** quand vous faites un lift-and-shift des packages basés sur des systèmes de fichiers locaux dans SSIS au sein d’Azure, effectuez les actions suivantes :
1.  Transférez les fichiers des systèmes de fichiers locaux vers Azure Files. Pour plus d’informations, consultez [Azure Files](https://azure.microsoft.com/services/storage/files/).
2.  Connectez votre runtime d’intégration Azure SSIS à Azure Files en configurant les informations d’identification d’accès qui utilisent l’authentification Windows. Pour plus d’informations, consultez [Se connecter à des données et des partages de fichiers avec l’authentification Windows](ssis-azure-connect-with-windows-auth.md).
3.  Mettez à jour les chemins de fichiers locaux de vos packages en fonction des chemins UNC qui pointent vers Azure Files. Par exemple, mettez à jour `C:\abc.txt` vers `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`.
