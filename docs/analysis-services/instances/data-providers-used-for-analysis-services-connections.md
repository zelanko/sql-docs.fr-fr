---
title: "Fournisseurs de données utilisés pour les connexions Analysis Services | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d6cd6ad8d29ba92b2da6149874b998f54c32a4af
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="data-providers-used-for-analysis-services-connections"></a>Fournisseurs de données utilisés pour les connexions Analysis Services
  Analysis Services fournit trois fournisseurs de données pour l'accès au serveur et aux données. Toutes les applications qui se connectent à Analysis Services le font à l'aide de l'un de ces fournisseurs. Deux des fournisseurs ADOMD.NET et Analysis Services Management Objects (AMO) sont des fournisseurs de données managés. Le fournisseur OLE DB Analysis Services (DLL MSOLAP) est un fournisseur de données natif.  
  
 Dans les organisations qui exécutent plusieurs versions d'Analysis Services, vous devrez peut-être installer les versions les plus récentes des fournisseurs de données sur les stations de travail des utilisateurs se connectant aux données Analysis Services. Les connexions aux versions les plus récentes d'Analysis Services nécessitent les fournisseurs de données de la même version principale. Par exemple, pour une connexion à [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], chaque station de travail doit disposer d’un fournisseur de données de la même version. Bien que l'application Excel installe les fournisseurs de données auxquels elle doit se connecter, le fournisseur peut être obsolète par rapport aux instances Analysis Services que vous utilisez.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Procédure pour déterminer la version du serveur](#bkmk_ServVers)  
  
 [Procédure : déterminer la version des fournisseurs de données Analysis Services](#bkmk_LibUpdate)  
  
 [Où obtenir une version plus récente des fournisseurs de données](#bkmk_downloadsite)  
  
 [Fournisseur OLE DB Analysis Services](#bkmk_OLE)  
  
 [ADOMD.NET](#bkmk_ADOMD)  
  
 [AMO](#blkmk_AMO)  
  
##  <a name="bkmk_ServVers"></a> Procédure pour déterminer la version du serveur  
 Connaître la version de l'instance d'Analysis Services vous aidera à déterminer si vous devez installer les versions les plus récentes des fournisseurs de données sur les stations de travail de votre organisation.  
  
-   Dans SQL Server Management Studio, connectez-vous à l'instance d'Analysis Services. Vous pouvez afficher des informations de version dans **Propriétés du serveur** > **Général** > **Version**.  
  
 Le numéro de la build majeure de la version initiale de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est 13.0.1601.5.  
  
  
##  <a name="bkmk_LibUpdate"></a> Procédure : déterminer la version des fournisseurs de données Analysis Services  
 Les fournisseurs de données sont installés avec Analysis Services, ainsi que par les applications clientes qui se connectent régulièrement à des bases de données Analysis Services, comme Excel.  
  
 Office 2010 installe les fournisseurs de données SQL Server 2008. Office 2013 installe les fournisseurs de données de SQL Server 2012, etc. Si vous utilisez plusieurs versions d'Office ou de SQL Server, et que les connexions ou la disponibilité des fonctionnalités ne correspondent pas à vos attentes, vous devrez peut-être installer une version plus récente des fournisseurs de données. Vous pouvez exécuter plusieurs versions principales de chaque fournisseur de données côte à côte sur le même ordinateur.  
  
#### <a name="find-the-file-version-of-the-oledb-provider"></a>Rechercher la version de fichier du fournisseur OLEDB  
  
1.  Accédez au dossier \Program Files\Microsoft Analysis Services\AS OLEDB\130.  
  
2.  Cliquez avec le bouton droit sur **msolap130.dll** > **Propriétés** > **Détails**.  
  
 Si vous ne parvenez pas à trouver le fichier à cet emplacement, ou si le chemin d'accès au dossier inclut AS OLEDB\110 ou AS OLEDB\90, c'est que vous utilisez une bibliothèque plus ancienne et que vous devez maintenant installer une version plus récente (AS OLEDB\11) pour vous connecter à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
#### <a name="find-the-file-version-of-adomdnet-and-amo"></a>Rechercher la version du fichier d'ADOMD.NET et d'AMO  
  
1.  Accédez à C:\Windows\Assembly  
  
2.  Cliquez avec le bouton droit sur Microsoft.AnalysisServices.AdomdClient, puis cliquez sur **Propriétés**. Cliquez sur **Version**.  
  
     Pour AMO, cliquez avec le bouton droit sur Microsoft.AnalysisServices.  
  
##  <a name="bkmk_downloadsite"></a> Où obtenir une version plus récente des fournisseurs de données  
 La version installée sur l'ordinateur client doit correspondre à la version principale du serveur qui fournit les données. Si l'installation du serveur est plus récente que les fournisseurs de données installés sur les stations de travail de votre réseau, vous devrez peut-être installer les dernières bibliothèques disponibles.  
  
#### <a name="find-the-data-providers-on-the-download-site"></a>Recherche les fournisseurs de données sur le site de téléchargement  
  
1.  Accédez au [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=52676).  
  
2.  Cliquez sur **Télécharger**. ADOMD.NET, le fournisseur OLE DB et AMO sont inclus dans la liste en tant qu’un package d’installation. Par exemple, SQL_AS_OLEDB.msi. Chaque bibliothèque est disponible dans les versions 32 bits ou 64 bits. Les serveurs et les stations de travail les plus récentes exécutant un système d'exploitation à 64 bits nécessiteront la version 64 bits.  
  
##  <a name="bkmk_OLE"></a> Fournisseur OLE DB Analysis Services  
 Le fournisseur OLE DB pour Analysis Services est le fournisseur natif de connexions de la base de données Analysis Services. MSOLAP est utilisé indirectement par ADOMD.NET et AMO, par délégation des demandes de connexion au fournisseur de données. Vous pouvez également appeler le fournisseur OLE DB directement à partir du code de l'application, notamment si les spécifications relatives à la solution excluent l'utilisation d'une API managée.  
  
 Le fournisseur OLE DB pour Analysis Services est installé automatiquement par le programme d'installation de SQL Server, Excel et d'autres applications fréquemment utilisées pour accéder aux bases de données Analysis Services. Vous pouvez également l'installer manuellement en le téléchargeant depuis le Centre de téléchargement. Par défaut, le fournisseur est disponible dans le dossier \Program Files\Microsoft Analysis Services. Le fournisseur doit être installé sur toutes les stations de travail utilisées pour accéder aux données Analysis Services.  
  
 MSOLAP130.dll correspond à la version du fournisseur OLE DB Analysis Services fournie avec [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les versions précédentes récentes incluent MSOLAP110.dll (pour SQL Server 2008 et 2008 R2) et MSOLAP90.dll (pour SQL Server 2005).  
  
 Les fournisseurs OLE DB sont souvent spécifiés dans les chaînes de connexion. Une chaîne de connexion Analysis Services utilise une autre nomenclature pour faire référence au fournisseur OLE DB : MSOLAP. \<version > .dll  
  
 MSOLAP.5.dll correspond au fournisseur OLE DB Analysis Services installé avec Excel 2013. Les versions précédentes, telles que MSOLAP.4.dll ou MSOLAP.3.dll, sont souvent disponibles sur des stations de travail qui exécutent des versions antérieures d'Excel. Certaines fonctionnalités Analysis Services, telles que le complément [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], requièrent des versions spécifiques du fournisseur OLE DB. Pour plus d’informations, consultez [Propriétés des chaînes de connexion &#40;Analysis Services&#41;](../../analysis-services/instances/connection-string-properties-analysis-services.md).  
  
##  <a name="bkmk_ADOMD"></a> ADOMD.NET  
 ADOMD.NET est un fournisseur de données managé utilisé pour interroger des données Analysis Services. Excel utilise ADOMD.NET lors de la connexion à un cube Analysis Services spécifique. La chaîne de connexion que vous voyez dans Excel convient pour une connexion ADOMD.NET.  
  
 ADOMD.NET est installé par le programme d'installation de SQL Server et est utilisé par les applications clientes SQL Server pour la connexion à Analysis Services. Office installe cette bibliothèque pour prendre en charge les connexions de données à partir d'Excel. Comme avec les autres fournisseurs de données inclus dans SQL Server, vous pouvez redistribuer ADOMD.NET si vous utilisez la bibliothèque dans du code personnalisé. Vous pouvez également le télécharger et l’installer manuellement pour obtenir la nouvelle version (consultez [Procédure : déterminer la version des fournisseurs de données Analysis Services](#bkmk_LibUpdate) , dans cette rubrique).  
  
 Pour vérifier la version du fichier, recherchez ADOMD.NET dans le GAC (Global Assembly Cache), où il figure en tant que `Microsoft.AnalysisServices.AdomdClient`.  
  
 Lors de la connexion à une base de données, les propriétés de chaîne de connexion pour les trois bibliothèques sont essentiellement les mêmes. Presque n’importe quelle chaîne de connexion que vous définissez pour ADOMD.NET (<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>) fonctionne également pour AMO et pour le fournisseur OLE DB Analysis Services. Pour plus d’informations, consultez [Propriétés des chaînes de connexion &#40;Analysis Services&#41;](../../analysis-services/instances/connection-string-properties-analysis-services.md).  
  
 Pour plus d’informations sur la connexion par programmation, consultez [Établissement de connexions dans ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md).  
  
##  <a name="blkmk_AMO"></a> AMO  
 AMO est un fournisseur de données managé utilisé pour l'administration du serveur et la définition de données. Par exemple, SQL Server Management Studio utilise AMO pour la connexion à Analysis Services.  
  
 AMO est installé par le programme d'installation de SQL Server et est utilisé par les applications clientes SQL Server pour la connexion à Analysis Services. Vous pouvez également le télécharger et l’installer manuellement quand vous utilisez AMO dans du code personnalisé (consultez [Procédure : déterminer la version des fournisseurs de données Analysis Services](#bkmk_LibUpdate) , dans cette rubrique). AMO est disponible dans le Global Assembly Cache (GAC) en tant que `Microsoft.AnalysisServices`.  
  
 Une connexion à l’aide d’AMO est généralement minimaliste, consistant en « source de données =\<nom_serveur > ». Une fois la connexion établie, utilisez l'API pour travailler avec des collections et les objets principaux de base de données. SSDT et SSMS emploient AMO pour se connecter à une instance d'Analysis Services.  
  
 Pour plus d’informations sur la connexion par programmation, consultez [Programmation d’objets fondamentaux AMO](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-fundamental-objects.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  

