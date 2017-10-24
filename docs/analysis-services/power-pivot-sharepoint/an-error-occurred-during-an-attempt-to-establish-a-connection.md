---
title: "Une erreur s’est produite lors d’une tentative pour établir une connexion | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 226842eb86c8eb7d5981407c805e18495dfb2579
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection"></a>Une erreur s’est produite lors d’une tentative pour établir une connexion
  Cette erreur se produit si vous interrogez des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sur un serveur sur lequel [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint n’est pas installé. Elle se produit également si le service SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) est arrêté, ou si vous essayez d’afficher des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] d’une version antérieure.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|La connexion de données a échoué.|  
|Texte du message|Une erreur s'est produite lors de la tentative de connexion à la source de données externe. Échec de l’actualisation des connexions suivantes : données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
  
## <a name="explanation"></a>Explication  
 Excel Services retourne cette erreur quand vous interrogez des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans un classeur Excel qui est publié dans SharePoint et que l’environnement SharePoint ne dispose pas d’un serveur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint, ou si le service SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) est arrêté.  
  
 L’erreur se produit lorsque vous découpez ou filtrez des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] alors que le moteur d’interrogation n’est pas disponible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Installez [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint ou déplacez le classeur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] vers un environnement SharePoint dans lequel [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint est installé. Pour plus d’informations, voir [Installation de PowerPivot pour SharePoint 2010](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f).  
  
 Si le logiciel est installé, vérifiez que l’instance SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) est en cours d’exécution. Sélectionnez **Gérer les services sur le serveur** dans Administration centrale. Sélectionnez également l'application de console Services dans Outils d'administration.  
  
 Pour les classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] créés dans une version SQL Server 2008 R2 de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour Excel, vous devez installer la version SQL Server 2008 R2 du fournisseur OLE DB Analysis Services. Cette erreur se produira si vous avez installé le fournisseur, mais n'avez pas enregistré le fichier Microsoft.AnalysisServices.ChannelTransport.dll. Pour plus d’informations sur l’enregistrement du fichier, consultez [Installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
## <a name="see-also"></a>Voir aussi  
 [La connexion de données utilise l’authentification Windows et les informations d’identification de l’utilisateur n’a pas pu être déléguées. Impossible d’actualiser les connexions suivantes : données Power Pivot](../../analysis-services/power-pivot-sharepoint/the-data-connection-user-could-not-be-delegated.md)  
  
  

