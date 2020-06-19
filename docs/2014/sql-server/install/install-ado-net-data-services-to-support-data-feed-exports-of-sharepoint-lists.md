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
ms.openlocfilehash: fb47804daee38427f48baefdf3997edda5fb90b1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054762"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Installation d'ADO.NET Data Services pour prendre en charge les exportations de flux de données des listes SharePoint
  ADO.NET Data Services est requis pour une exportation de flux de données de listes SharePoint. SharePoint 2010 n'inclut pas ce composant dans le programme d'installation des composants requis pour SharePoint. Par conséquent, vous devez l'installer manuellement.  
  
 Sans ce composant requis, vous obtenez l'erreur suivante lorsque vous essayez d'utiliser une liste SharePoint exportée en tant que flux de données : « pour des raisons de sécurité, la DTD est interdite dans ce document XML. Pour activer le traitement DTD, affectez à la propriété ProhibitDtd de XmlReaderSettings la valeur False et transmettez les paramètres à la méthode XmlReader.Create ».  
  
 Utilisez les instructions suivantes pour installer ADO.NET Data Services sur chaque serveur SharePoint pour lequel vous voulez autoriser l'exportation de listes en tant que flux de données.  
  
### <a name="download-and-install-adonet-data-services"></a>Télécharger et installer ADO.NET Data Services  
  
1.  Accédez à la documentation relative à la configuration matérielle et logicielle requise pour SharePoint 2010, [Configuration matérielle et logicielle requise (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  Dans **accès aux logiciels applicables**, recherchez le lien pour ADO.NET Data Services 3,5 qui correspond au système d’exploitation que vous utilisez (windows Server 2008 SP2 ou windows Server 2008 R2).  
  
3.  Cliquez sur le lien, puis exécutez le programme d'installation qui installe le service.  
  
## <a name="see-also"></a>Voir aussi  
 [PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
