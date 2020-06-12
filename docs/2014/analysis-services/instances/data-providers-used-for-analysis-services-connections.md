---
title: Fournisseurs de données utilisés pour les connexions Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a48316bb89f92ba8b44e3160a6b38e77762f3be
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543981"
---
# <a name="data-providers-used-for-analysis-services-connections"></a>Fournisseurs de données utilisés pour les connexions Analysis Services
  Analysis Services fournit trois fournisseurs de données pour l'accès au serveur et aux données. Toutes les applications qui se connectent à Analysis Services le font à l'aide de l'un de ces fournisseurs. Deux des fournisseurs ADOMD.NET et Analysis Services Management Objects (AMO) sont des fournisseurs de données managés. Le fournisseur OLE DB Analysis Services (DLL MSOLAP) est un fournisseur de données natif.  
  
 Dans les organisations qui exécutent plusieurs versions d'Analysis Services, vous devrez peut-être installer les versions les plus récentes des fournisseurs de données sur les stations de travail des utilisateurs se connectant aux données Analysis Services. Les connexions aux versions les plus récentes d'Analysis Services nécessitent les fournisseurs de données de la même version principale. Par exemple, pour une connexion à [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], chaque station de travail doit disposer d'un fournisseur de données de la version 2014. Bien que l'application Excel installe les fournisseurs de données auxquels elle doit se connecter, le fournisseur peut être obsolète par rapport aux instances Analysis Services que vous utilisez.  
  
 Cette rubrique contient la section suivante :  
  
 [Procédure pour déterminer la version du serveur](#bkmk_ServVers)  
  
 [Procédure : déterminer la version des fournisseurs de données Analysis Services](#bkmk_LibUpdate)  
  
 [Où obtenir une version plus récente des fournisseurs de données](#bkmk_downloadsite)  
  
 [Fournisseur OLE DB Analysis Services](#bkmk_OLE)  
  
 [ADOMD.NET](#bkmk_ADOMD)  
  
 [AMO](#blkmk_AMO)  
  
##  <a name="how-to-determine-server-version"></a><a name="bkmk_ServVers"></a>Comment déterminer la version du serveur  
 Connaître la version de l'instance d'Analysis Services vous aidera à déterminer si vous devez installer les versions les plus récentes des fournisseurs de données sur les stations de travail de votre organisation.  
  
-   Dans SQL Server Management Studio, connectez-vous à l'instance d'Analysis Services. Cliquez avec le bouton droit sur l’instance que vous souhaitez vérifier, pointez sur **rapports**, puis cliquez sur **général**. Les informations de version et d'édition s'affichent dans le rapport.  
  
 Le numéro de la version principale de la version initiale de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est 12.0.2000.9.  
  
 Pour plus d’informations sur l’obtention des informations de version et de build, consultez [Comment déterminer la version et l’édition de SQL Server et de ses composants](https://support.microsoft.com/kb/321185).  
  
##  <a name="how-to-determine-the-version-of-the-analysis-services-data-providers"></a><a name="bkmk_LibUpdate"></a>Comment déterminer la version des fournisseurs de données Analysis Services  
 Les fournisseurs de données sont installés avec Analysis Services, ainsi que par les applications clientes qui se connectent régulièrement à des bases de données Analysis Services, comme Excel.  
  
 Office 2007 installe les fournisseurs de données SQL Server 2005. Office 2010 installe les fournisseurs de données SQL Server 2008. Office 2013 installe les fournisseurs de données SQL Server 2012. Si vous utilisez plusieurs versions d'Office ou de SQL Server, et que les connexions ou la disponibilité des fonctionnalités ne correspondent pas à vos attentes, vous devrez peut-être installer une version plus récente des fournisseurs de données. Vous pouvez exécuter plusieurs versions principales de chaque fournisseur de données côte à côte sur le même ordinateur.  
  
#### <a name="find-the-file-version-of-the-oledb-provider"></a>Rechercher la version de fichier du fournisseur OLEDB  
  
1.  Accédez au dossier \Program Files\Microsoft Analysis Services\AS OLEDB\120.  
  
2.  Cliquez avec le bouton droit sur msolap120.dll, puis cliquez sur **Propriétés**.  
  
 Si vous ne parvenez pas à trouver le fichier à cet emplacement, ou si le chemin d'accès au dossier inclut AS OLEDB\110 ou AS OLEDB\90, c'est que vous utilisez une bibliothèque plus ancienne et que vous devez maintenant installer une version plus récente (AS OLEDB\11) pour vous connecter à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
#### <a name="find-the-file-version-of-adomdnet-and-amo"></a>Rechercher la version du fichier d'ADOMD.NET et d'AMO  
  
1.  Accédez à C:\Windows\Assembly  
  
2.  Cliquez avec le bouton droit sur Microsoft.AnalysisServices.AdomdClient, puis cliquez sur **Propriétés**. Cliquez sur **Version**.  
  
     Pour AMO, cliquez avec le bouton droit sur Microsoft.AnalysisServices.  
  
 Pour plus d’informations sur les numéros de version et de build par version, consultez [SQL Server builds sur blogspot](http://sqlserverbuilds.blogspot.com).  
  
##  <a name="where-to-get-newer-version-data-providers"></a><a name="bkmk_downloadsite"></a>Où se procurer des fournisseurs de données de version plus récente  
 La version installée sur l'ordinateur client doit correspondre à la version principale du serveur qui fournit les données. Si l'installation du serveur est plus récente que les fournisseurs de données installés sur les stations de travail de votre réseau, vous devrez peut-être installer les dernières bibliothèques disponibles.  
  
#### <a name="find-the-data-providers-on-the-download-site"></a>Recherche les fournisseurs de données sur le site de téléchargement  
  
1.  Accédez au [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkID=296473).  
  
2.  Développez **Instructions d’installation**.  
  
3.  Faites défiler vers le bas jusqu'à la section contenant les composants Analysis Services. ADOMD.NET, le fournisseur OLE DB et AMO sont respectivement les deuxième, troisième et quatrième éléments de la liste. Chaque bibliothèque est disponible dans les versions 32 bits ou 64 bits. Les serveurs et les stations de travail les plus récentes exécutant un système d'exploitation à 64 bits nécessiteront la version 64 bits.  
  
##  <a name="analysis-services-ole-db-provider"></a><a name="bkmk_OLE"></a>Fournisseur Analysis Services OLE DB  
 Le fournisseur OLE DB pour Analysis Services est le fournisseur natif de connexions de la base de données Analysis Services. MSOLAP est utilisé indirectement par ADOMD.NET et AMO, par délégation des demandes de connexion au fournisseur de données. Vous pouvez également appeler le fournisseur OLE DB directement à partir du code de l'application, notamment si les spécifications relatives à la solution excluent l'utilisation d'une API managée.  
  
 Le fournisseur OLE DB pour Analysis Services est installé automatiquement par le programme d'installation de SQL Server, Excel et d'autres applications fréquemment utilisées pour accéder aux bases de données Analysis Services. Vous pouvez également l'installer manuellement en le téléchargeant depuis le Centre de téléchargement. Par défaut, le fournisseur est disponible dans le dossier \Program Files\Microsoft Analysis Services. Le fournisseur doit être installé sur toutes les stations de travail utilisées pour accéder aux données Analysis Services.  
  
 MSOLAP130.dll correspond à la version du fournisseur OLE DB Analysis Services fournie avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les versions précédentes récentes incluent MSOLAP10.dll (pour SQL Server 2008 et 2008 R2) et MSOLAP90.dll (pour SQL Server 2005).  
  
 Les fournisseurs OLE DB sont souvent spécifiés dans les chaînes de connexion. Une chaîne de connexion Analysis Services utilise une autre nomenclature pour faire référence au fournisseur de OLE DB : MSOLAP. \<version> . dll  
  
 MSOLAP.5.dll correspond au fournisseur OLE DB Analysis Services installé avec Excel 2013. Les versions précédentes, telles que MSOLAP.4.dll ou MSOLAP.3.dll, sont souvent disponibles sur des stations de travail qui exécutent des versions antérieures d'Excel. Certaines fonctionnalités Analysis Services, telles que le complément PowerPivot, requièrent des versions spécifiques du fournisseur OLE DB. Pour plus d’informations, consultez [Propriétés des chaînes de connexion &#40;Analysis Services&#41;](connection-string-properties-analysis-services.md).  
  
##  <a name="adomdnet"></a><a name="bkmk_ADOMD"></a>ADOMD.NET  
 ADOMD.NET est un fournisseur de données managé utilisé pour interroger des données Analysis Services. Excel utilise ADOMD.NET lors de la connexion à un cube Analysis Services spécifique. La chaîne de connexion que vous voyez dans Excel convient pour une connexion ADOMD.NET.  
  
 ADOMD.NET est installé par le programme d'installation de SQL Server et est utilisé par les applications clientes SQL Server pour la connexion à Analysis Services. Office installe cette bibliothèque pour prendre en charge les connexions de données à partir d'Excel. Comme avec les autres fournisseurs de données inclus dans SQL Server, vous pouvez redistribuer ADOMD.NET si vous utilisez la bibliothèque dans du code personnalisé. Vous pouvez également le télécharger et l’installer manuellement pour obtenir la nouvelle version (consultez [Procédure : déterminer la version des fournisseurs de données Analysis Services](#bkmk_LibUpdate) , dans cette rubrique).  
  
 Pour vérifier la version du fichier, recherchez ADOMD.NET dans le GAC (Global Assembly Cache), où il figure en tant que `Microsoft.AnalysisServices.AdomdClient`.  
  
 Lors de la connexion à une base de données, les propriétés de chaîne de connexion pour les trois bibliothèques sont essentiellement les mêmes. Presque n’importe quelle chaîne de connexion que vous définissez pour ADOMD.NET (<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>) fonctionne également pour AMO et pour le fournisseur OLE DB Analysis Services. Pour plus d’informations, consultez [Propriétés des chaînes de connexion &#40;Analysis Services&#41;](connection-string-properties-analysis-services.md).  
  
 Pour plus d’informations sur la connexion par programmation, consultez [Établissement de connexions dans ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/connections-in-adomd-net).  
  
##  <a name="amo"></a><a name="blkmk_AMO"></a>AMO  
 AMO est un fournisseur de données managé utilisé pour l'administration du serveur et la définition de données. Par exemple, SQL Server Management Studio utilise AMO pour la connexion à Analysis Services.  
  
 AMO est installé par le programme d'installation de SQL Server et est utilisé par les applications clientes SQL Server pour la connexion à Analysis Services. Vous pouvez également le télécharger et l’installer manuellement quand vous utilisez AMO dans du code personnalisé (consultez [Procédure : déterminer la version des fournisseurs de données Analysis Services](#bkmk_LibUpdate) , dans cette rubrique). AMO est disponible dans le Global Assembly Cache (GAC) en tant que `Microsoft.AnalysisServices`.  
  
 Une connexion à l’aide d’AMO est généralement minime, composée de « Data source = \<servername> ». Une fois une connexion établie, vous utilisez l’API pour recourir à des collections de bases de données et à des objets principaux. SSDT et SSMS utilisent AMO pour se connecter à une instance Analysis Services.  
  
 Pour plus d’informations sur la connexion par programmation, consultez [Programmation d’objets fondamentaux AMO](https://docs.microsoft.com/bi-reference/amo/programming-amo-fundamental-objects).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à Analysis Services](connect-to-analysis-services.md)  
  
  
