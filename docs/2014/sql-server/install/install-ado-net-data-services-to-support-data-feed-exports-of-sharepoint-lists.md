---
title: Installer ADO.NET Data Services pour prendre en charge les exportations de flux de données des listes SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: b9b3ec2d8b7459f9d66313c6a40b1cbc26450e0d
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952162"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Installation d'ADO.NET Data Services pour prendre en charge les exportations de flux de données des listes SharePoint
  ADO.NET Data Services est requis pour une exportation de flux de données de listes SharePoint. SharePoint 2010 n'inclut pas ce composant dans le programme d'installation des composants requis pour SharePoint. Par conséquent, vous devez l'installer manuellement.  
  
 Sans cette condition préalable, vous obtiendrez l’erreur suivante lorsque vous tentez d’utiliser une liste SharePoint exportée en tant que flux de données : «Pour des raisons de sécurité, la DTD est interdite dans ce document XML. Pour activer le traitement DTD, affectez à la propriété ProhibitDtd de XmlReaderSettings la valeur False et transmettez les paramètres à la méthode XmlReader.Create ».  
  
 Utilisez les instructions suivantes pour installer ADO.NET Data Services sur chaque serveur SharePoint pour lequel vous voulez autoriser l'exportation de listes en tant que flux de données.  
  
### <a name="download-and-install-adonet-data-services"></a>Télécharger et installer ADO.NET Data Services  
  
1.  Accédez à la documentation relative à la configuration matérielle et logicielle requise pour SharePoint 2010, [Configuration matérielle et logicielle requise (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  Dans **accès aux logiciels applicables**, recherchez le lien pour ADO.NET Data Services 3,5 qui correspond au système d’exploitation que vous utilisez (windows Server 2008 SP2 ou windows Server 2008 R2).  
  
3.  Cliquez sur le lien, puis exécutez le programme d'installation qui installe le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
