---
title: "Une erreur s'est produite lors de la tentative de connexion à la source de données externe. Échec de l’actualisation des connexions suivantes : données PowerPivot | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 242fefb2ca22d7b0129268a8a3ea8ed98e80bbe3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547611"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection-to-the-external-data-source-the-following-connections-failed-to-refresh-powerpivot-data"></a>Une erreur s'est produite lors de la tentative de connexion à la source de données externe. Échec de l'actualisation des connexions suivantes : Données PowerPivot
  Cette erreur se produit si vous interrogez des données PowerPivot sur un serveur sur lequel PowerPivot pour SharePoint n'est pas installé. Se produit également si le service SQL Server Analysis Services (PowerPivot) est arrêté, ou si vous essayez d'afficher des données PowerPivot d'une version antérieure.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S’applique à|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|La connexion de données a échoué.|  
|Texte du message|Une erreur s'est produite lors de la tentative de connexion à la source de données externe. Échec de l'actualisation des connexions suivantes : Données PowerPivot|  
  
## <a name="explanation"></a>Explication  
 Excel Services retourne cette erreur lorsque vous interrogez des données PowerPivot dans un classeur Excel qui est publié dans SharePoint et que l'environnement SharePoint ne dispose pas d'un serveur PowerPivot pour SharePoint, ou si le service SQL Server Analysis Services (PowerPivot) est arrêté.  
  
 L'erreur se produit lorsque vous découpez ou filtrez des données PowerPivot alors que le moteur d'interrogation n'est pas disponible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Installez PowerPivot pour SharePoint ou déplacez le classeur PowerPivot vers un environnement SharePoint dans lequel PowerPivot pour SharePoint est installé. Pour plus d'informations, consultez [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md).  
  
 Si le logiciel est installé, vérifiez que l'instance SQL Server Analysis Services (PowerPivot) s'exécute. Sélectionnez **Gérer les services sur le serveur** dans Administration centrale. Sélectionnez également l'application de console Services dans Outils d'administration.  
  
 Pour les classeurs PowerPivot créés dans une version SQL Server 2008 R2 PowerPivot pour Excel, vous devez installer la version SQL Server 2008 R2 du fournisseur OLE DB Analysis Services. Cette erreur se produira si vous avez installé le fournisseur, mais n'avez pas enregistré le fichier Microsoft.AnalysisServices.ChannelTransport.dll. Pour plus d’informations sur l’enregistrement du fichier, consultez [Installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [La connexion de données utilise l’authentification Windows et les informations d’identification de l’utilisateur n’ont pas pu être déléguées. Échec de l’actualisation des connexions suivantes : données PowerPivot](the-data-connection-user-could-not-be-delegated.md)  
  
  
