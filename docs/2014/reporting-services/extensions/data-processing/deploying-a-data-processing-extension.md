---
title: Déploiement d’une extension pour le traitement des données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
caps.latest.revision: 34
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 63628c1be1803833a65875ddf75d4434af38c87f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143844"
---
# <a name="deploying-a-data-processing-extension"></a>Déploiement d'une extension pour le traitement des données
  Une fois que vous avez écrit et compilé votre extension pour le traitement des données [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dans une bibliothèque [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], vous devez la rendre détectable par le serveur de rapports et par le Concepteur de rapports. Cette opération est aussi simple que de copier l'extension vers les répertoires appropriés et d'ajouter des entrées aux fichiers de configuration [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] appropriés.  
  
## <a name="configuration-file-extension-element"></a>Élément Extension du fichier de configuration  
 Les extensions pour le traitement des données que vous déployez sur le serveur de rapports ou le Concepteur de rapports doivent être entrées en tant qu’éléments **Extension** dans les fichiers de configuration. Ces fichiers sont RSReportServer.config pour le serveur de rapports et RSReportDesigner.config pour le Générateur de rapports.  
  
 Le tableau suivant décrit les attributs de l’élément **Extension** pour les extensions pour le traitement des données.  
  
|Attribute|Description|  
|---------------|-----------------|  
|`Name`|Nom unique de l'extension, par exemple, « SQL » pour l'extension pour le traitement des données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ou « OLEDB » pour l'extension pour le traitement des données OLE DB. La longueur maximale de l'attribut `Name` s'élève à 255 caractères. Le nom doit être unique au sein de toutes les entrées de l’élément **Extension** d’un fichier de configuration.|  
|`Type`|Liste séparée par des virgules qui inclut l'espace de noms complet, ainsi que le nom de l'assembly.|  
|`Visible`|La valeur `false` indique que l'extension pour le traitement des données ne doit pas être visible dans les interfaces utilisateur. Si l’attribut n’est pas inclus, la valeur par défaut est `true`.|  
  
 Pour plus d’informations sur les fichiers RSReportServer.config ou RSReportDesigner.config, consultez [Fichiers de configuration de Reporting Services](../../report-server/reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Procédure : déployer une extension pour le traitement des données sur un serveur de rapports](deploying-a-data-processing-extension-to-a-report-server.md)|Décrit comment déployer votre extension pour le traitement des données sur un serveur de rapports.|  
|[Procédure : déployer une extension pour le traitement des données sur le Concepteur de rapports](deploying-a-data-processing-extension-to-report-designer.md)|Décrit comment déployer votre extension pour le traitement des données sur le Générateur de rapports.|  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../reporting-services-extensions.md)   
 [Implémentation d’une extension pour le traitement des données](implementing-a-data-processing-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../reporting-services-extension-library.md)  
  
  