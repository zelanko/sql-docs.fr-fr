---
title: Installation de SMO | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1a0c23d91785a453bcbf7857211e524b15a4ec3f
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008590"
---
# <a name="installing-smo"></a>Installation de SMO

[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

Cette page fournit des informations sur l’installation de SMO pour une utilisation par les applications et la configuration requise pour utiliser SMO.

## <a name="smo-nuget-package"></a>Package NuGet SMO

À partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 Smo est distribué en tant que package NuGet [Microsoft. SqlServer. SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) pour permettre aux utilisateurs de développer des applications avec Smo.

Il s’agit d’un remplacement de SharedManagementObjects.msi, qui a été précédemment publié dans le cadre du Feature Pack SQL pour chaque version de SQL Server. Les applications qui utilisent SMO doivent être mises à jour pour utiliser le package NuGet à la place et doivent s’assurer que les fichiers binaires sont installés avec l’application en cours de développement.

>>[!Important]
>>Comme mentionné dans la page [fichiers et numéros de version](files-and-version-numbers.md) , vous ne devez pas installer les assemblys Smo dans le GAC. Cela peut entraîner des problèmes avec d’autres applications qui utilisent également ces versions de SMO (par exemple, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

## <a name="installing-the-package"></a>Installation du package

Consultez [NuGet démarrage rapide-utilisation d’un package](https://docs.microsoft.com/nuget/quickstart/use-a-package) pour obtenir des instructions et des exemples d’installation et d’utilisation d’un package NuGet. 
  
## <a name="system-requirements"></a>Configuration système requise
  
 SMO requiert [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] l’exécution de 4,0 ou .net Core 2,0, donc toutes les applications qui l’utilisent doivent s’assurer que cette version ou une version ultérieure est installée sur les ordinateurs clients. Certains binaires natifs installés avec les bibliothèques SMO NetFx nécessitent également l’installation du runtime VC 2013. ce Runtime n’est pas inclus dans le package. Vous pouvez télécharger le package Redist approprié à votre architecture cible à partir dehttps://www.microsoft.com/download/details.aspx?id=40784
  
