---
title: Accès aux données PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 83dc82da-91fb-4e47-91a8-0e0db67339b8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f5d2045601f72c3536fbf2d4e469eb5eb20fbe
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66071251"
---
# <a name="powerpivot-data-access"></a>Accès aux données PowerPivot
  Cette rubrique décrit les manières dont les données sont récupérées à partir d'un classeur PowerPivot publié dans une bibliothèque SharePoint.  
  
 Les données PowerPivot sont stockées dans un classeur Excel. La chaîne de connexion est une URL vers un classeur sur un site SharePoint.  
  
 Les données PowerPivot sont le plus souvent utilisées par le classeur qui les contient, notamment les données sous-jacentes des tableaux croisés dynamiques et des graphiques croisés dynamiques. Les données PowerPivot peuvent également être utilisées comme source de données externe, auquel cas un classeur, un tableau de bord ou un rapport se connecte à un fichier Excel (.xlsx) distinct dans SharePoint et récupère les données pour une utilisation ultérieure. Les outils clients qui utilisent généralement des données PowerPivot sont Excel, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], les autres rapports Reporting Services et PerformancePoint.  
  
 Sur le bureau, le complément PowerPivot utilise AMO et ADOMD.NET pour créer, traiter, et interroger les données PowerPivot dans l'espace de travail client.  
  
 Sur une batterie de serveurs SharePoint, Excel Services utilise le fournisseur OLE DB MSOLAP local pour la connexion aux données PowerPivot. Le fournisseur envoie la demande de connexion à un serveur PowerPivot pour SharePoint de la batterie. Ce serveur charge les données, exécute la requête, et retourne l'ensemble de résultats.  
  
##  <a name="querying-powerpivot-data-in-sharepoint"></a><a name="queryproc"></a>Interrogation des données PowerPivot dans SharePoint  
 Lorsque vous affichez un classeur PowerPivot à partir d'une bibliothèque SharePoint, les données PowerPivot contenues dans le classeur sont détectées, extraites et traitées séparément sur les instances du serveur Analysis Services de la batterie de serveurs, tandis qu'Excel Services restitue la couche présentation. Vous pouvez afficher le classeur pleinement traité dans une fenêtre de navigateur ou dans une application bureautique Excel 2010 dotée du complément PowerPivot.  
  
 Le diagramme suivant illustre le parcours d'une demande de traitement de requêtes dans la batterie de serveurs. Étant donné que les données PowerPivot font partie d'un classeur Excel 2010, une demande de traitement de requêtes se présente lorsqu'un utilisateur ouvre un classeur Excel à partir d'une bibliothèque SharePoint et interagit avec un tableau croisé dynamique ou graphique croisé dynamique qui contient des données PowerPivot.  
  
 ![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")  
  
 Les composants Excel Services et PowerPivot pour SharePoint traitent des parties différentes du même fichier de classeur (.xlsx). Excel Services détecte les données PowerPivot et en demande le traitement par un serveur PowerPivot de la batterie. Le serveur PowerPivot alloue la demande à une instance du [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] , qui extrait les données du classeur dans la bibliothèque de contenu et charge les données. Les données stockées en mémoire font l'objet d'une nouvelle fusion dans le classeur rendu et sont retransmises à Excel Web Access en vue de leur présentation dans une fenêtre de navigateur.  
  
 Toutes les données d'un classeur PowerPivot ne sont pas gérées par PowerPivot pour SharePoint. Excel Services traite les tableaux et les données des cellules d'une feuille de calcul. Seuls les tableaux croisés dynamiques, graphiques croisés dynamiques et segments qui vont à l'encontre des données PowerPivot sont gérés par le service PowerPivot pour SharePoint.  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à Analysis Services](../instances/connect-to-analysis-services.md)   
 [Accès aux données de modèle tabulaire](../tabular-models/tabular-model-data-access.md)  
  
  
