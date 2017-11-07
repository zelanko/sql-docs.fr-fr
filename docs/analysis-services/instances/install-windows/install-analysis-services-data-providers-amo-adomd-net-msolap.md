---
title: "Installer les fournisseurs de données Analysis Services (AMO, ADOMD.NET, MSOLAP) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7aedabc-6af9-4698-a7a4-98f894001476
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bd6aa812228cce132b4180a8537ba853f3ea92a2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="install-analysis-services-data-providers-amo-adomdnet-msolap"></a>Installer les fournisseurs de données Analysis Services (AMO, ADOMD.NET, MSOLAP)
  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] est une version mise à jour des fournisseurs de données Analysis Services, comprenant ADOMD.Net, AMO et MSOLAP.  
  
 Dans la plupart des scénarios d’accès aux données reposant sur une requête, vous pouvez utiliser les anciennes versions existantes des fournisseurs de données déjà installés sur les systèmes clients pour accéder aux modèles tabulaires et multidimensionnels sur une instance de SQL Server 2016 Analysis Services, y compris les modèles tabulaires qui utilisent des fonctionnalités de SQL Server 2016. En règle générale, les applications clientes qui génèrent des requêtes, comme Excel, Reporting Services ou Tableau, n’exigent pas les tout derniers fournisseurs de données lors de l’accès à un modèle Analysis Services.  
  
 Les outils d’administration et de modélisation sont une exception à la règle, en tout cas en termes d’exigences de version pour les fournisseurs de données. Ces outils doivent comporter les fournisseurs de données qui ont été construits spécifiquement pour le serveur cible afin de manipuler des objets sur ce serveur. Par chance, les outils fournis avec [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] incluent automatiquement des fournisseurs de données conformes à la version actuelle du serveur.  L’installation de SQL Server Data Tools pour Visual Studio 2015 installe les fournisseurs de données pour SQL Server 2016 Analysis Services. De même, SQL Server 2016 Management Studio, qui utilise AMO et ADOMD.Net, installe les deux fournisseurs de données ciblant [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Un scénario appelant l’installation manuelle d’un fournisseur de données repose sur des applications ou des scripts personnalisés utilisant Analysis Services Management Objects (AMO). Cette version introduit un espace de noms refactorisé qui déplace les principaux objets, comme un serveur ou une base de données, vers un nouvel espace de noms (Microsoft.AnalysisServices.Core) faisant partie de l’assembly Microsoft.AnalysisServices.dll. Si vous avez un code ou des scripts personnalisés qui utilisent AMO, vous devez recompiler le code et mettre à jour manuellement AMO sur chaque serveur et station de travail cliente qui établit une connexion directe via AMO vers une instance SQL Server 2016 d’Analysis Services.  
  
## <a name="provider-list"></a>Liste des fournisseurs  
 La table ci-dessous décrit chaque fournisseur.  
  
||||  
|-|-|-|  
|Fournisseur|Nom du fichier|Version|  
|Objets AMO (Analysis Management Objects) Analysis Services|Microsoft.AnalysisServices.dll|13.0.0.0|  
|Analysis Services Core|Microsoft.AnalysisServices.Core.dll|13.0.0.0|  
|Analysis Services (ADOMD.NET)|Microsoft.AnalysisServices.AdomdClient.dll|13.0.0.0|  
|Fournisseur OLE DB pour Analysis Services (MSOLAP)|MSOLAP130.dll|13.0.0.0|  
  
## <a name="download-and-install-data-provider"></a>Télécharger et installer un fournisseur de données  
  
1.  Accédez à la [page de téléchargement de SQL Server 2016 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=398150).  
  
2.  Cliquez sur **Télécharger** pour activer l’installation des composants individuels.  
  
3.  Pour les ordinateurs 64 bits, sélectionnez tout ou partie des composants suivants (sinon choisissez l’équivalent x86) :  
  
    -   ENU\x64\SQL_AS_ADOMD.msi  
  
    -   ENU\x64\SQL_AS_AMO.msi  
  
    -   ENU\x64\SQL_AS_OLEDB.msi  
  
4.  Cliquez sur **Suivant** pour télécharger les fichiers.  
  
5.  Exécutez chaque programme pour installer le fournisseur. Les assemblys ADO. MD et AMO sont installés dans C:\Windows\assembly\GAC_MSIL. Le fournisseur OLE DB pour Analysis Services est installé dans C:\Program Files\Microsoft Analysis Services\AS OLEDB\130.  
  
## <a name="verify-installation"></a>Vérifier l'installation  
  
1.  Dans l’Explorateur de fichiers, accédez à C:\Windows\Assembly.  
  
2.  Cliquez avec le bouton droit sur Microsoft.AnalysisServices, puis sélectionnez **Propriétés**.  
  
3.  Cliquez sur **Version** pour confirmer la build la plus récente.  
  
  

