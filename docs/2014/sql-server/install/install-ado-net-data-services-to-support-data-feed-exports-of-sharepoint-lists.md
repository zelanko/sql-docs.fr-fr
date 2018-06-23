---
title: Installer ADO.NET Data Services pour prendre en charge les données exportations de flux des listes SharePoint | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: d4241d56aa3257bd0ec2cddf4b439a4939f8ab9f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042788"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Installation d'ADO.NET Data Services pour prendre en charge les exportations de flux de données des listes SharePoint
  ADO.NET Data Services est requis pour une exportation de flux de données de listes SharePoint. SharePoint 2010 n'inclut pas ce composant dans le programme d'installation des composants requis pour SharePoint. Par conséquent, vous devez l'installer manuellement.  
  
 Sans ce composant requis, vous obtenez l'erreur suivante lorsque vous essayez d'utiliser une liste SharePoint exportée en tant que flux de données : « pour des raisons de sécurité, la DTD est interdite dans ce document XML. Pour activer le traitement DTD, affectez à la propriété ProhibitDtd de XmlReaderSettings la valeur False et transmettez les paramètres à la méthode XmlReader.Create ».  
  
 Utilisez les instructions suivantes pour installer ADO.NET Data Services sur chaque serveur SharePoint pour lequel vous voulez autoriser l'exportation de listes en tant que flux de données.  
  
### <a name="download-and-install-adonet-data-services"></a>Télécharger et installer ADO.NET Data Services  
  
1.  Accédez à la documentation relative à la configuration requise matérielle et logicielle pour SharePoint 2010, [configurations matérielle et logicielle requise (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  Dans **accès aux logiciels applicables**, recherchez le lien pour ADO.NET Data Services 3.5 correspondant au système d’exploitation que vous utilisez (Windows Server 2008 SP2 ou Windows Server 2008 R2).  
  
3.  Cliquez sur le lien, puis exécutez le programme d'installation qui installe le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Installation PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  