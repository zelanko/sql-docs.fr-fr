---
title: Type de connexion Oracle (SSRS et Power BI Report Server)
description: Utilisez les informations de cet article sur le type de connexion Oracle pour savoir comment créer une source de données.
ms.date: 03/12/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 425f864e31f1280fd31852de44a40d5e2d5c61ef
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891719"
---
# <a name="oracle-connection-type-ssrs--power-bi-report-server"></a>Type de connexion Oracle (SSRS et Power BI Report Server)

Pour utiliser des données d'une base de données Oracle dans votre rapport, vous devez avoir un dataset basé sur une source de données de rapport de type Oracle. Ce type de source de données intégré utilise directement le fournisseur de données Oracle et requiert un composant logiciel client Oracle. Cet article explique comment télécharger et installer des pilotes pour Reporting Services, Power BI Report Server, le Générateur de rapports et Power BI Desktop.


Utilisez les informations de cet article pour créer une source de données. Pour obtenir des instructions détaillées, consultez [Ajouter et vérifier une connexion de données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md). 


## <a name="64-bit-drivers-for-the-report-servers"></a>Pilotes 64 bits pour les serveurs de rapports

Power BI Report Server et SQL Server Reporting Services 2016 (et versions ultérieures) utilisent l’**ODP.NET managé** pour les rapports paginés. Les étapes suivantes sont nécessaires seulement si vous utilisez des pilotes Oracle ODAC 12.2 (et versions ultérieures). En effet, pour les nouvelles installations effectuées dans le répertoire de base Oracle, ces pilotes sont installés par défaut dans une configuration qui n’est pas appliquée à l’échelle de la machine. Ces étapes supposent que vous avez installé les fichiers ODAC 18.x à l’emplacement c:\oracle64, et que la version des fichiers Oracle.ManagedDataAccess.dll et Oracle.DataAccess.dll est 4.122.18.3.

1. Sur le site de téléchargement Oracle, installez le [programme d'installation Oracle 64 bits ODAC Oracle (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdeploy-4242173.html). 
2. Inscrivez le client managé ODP.NET dans GAC :

    C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. Ajoutez les entrées du client managé ODP.NET à machine.config :

    C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /productversion:4.122.18.3

### <a name="power-bi-reports-use-unmanaged-odpnet"></a>Les rapports Power BI utilisent ODP.NET non managé

Les rapports Power BI utilisent **ODP.NET non managé**. Pour inscrire le client ODP.NET managé, procédez comme suit :

1. Inscrivez le client non managé ODP.NET dans GAC :

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. Ajoutez les entrées du client non managé ODP.NET à machine.config :

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3
 
## <a name="32-bit-drivers-for-report-builder"></a>Pilotes 32 bits pour le Générateur de rapports

Le Générateur de rapports utilise l’**ODP.NET managé** pour la création des rapports paginés. Les étapes suivantes sont nécessaires seulement si vous utilisez des pilotes Oracle ODAC 12.2 et ultérieur. En effet, pour les nouvelles installations effectuées dans le répertoire de base Oracle, ces pilotes sont installés par défaut dans une configuration qui n’est pas appliquée à l’échelle de la machine. Ces étapes supposent que vous avez installé les fichiers ODAC 18.x à l’emplacement c:\oracle32, et que la version du fichier Oracle.ManagedDataAccess.dll est 4.122.18.3.

1. Sur le site de téléchargement Oracle, installez le [programme d'installation Oracle 32 bits ODAC Oracle (OUI)](https://www.oracle.com/technetwork/topics/dotnet/downloads/odacdev-4242174.html).
2. Inscrivez le client managé ODP.NET dans GAC :

    C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\managed\common\Oracle.ManagedDataAccess.dll
3. Ajoutez les entrées du client managé ODP.NET à machine.config :

    C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odpm /frameworkversion:v4.0.30319 /productversion:4.122.18.3

## <a name="64-bit-and-32-bit-drivers-for-power-bi-desktop"></a>Pilotes 64 bits et 32 bits pour Power BI Desktop

Les rapports Power BI utilisent **ODP.NET non managé**. Les étapes suivantes sont nécessaires seulement si vous utilisez des pilotes Oracle ODAC 12.2 et ultérieur. En effet, pour les nouvelles installations effectuées dans le répertoire de base Oracle, ces pilotes sont installés par défaut dans une configuration qui n’est pas appliquée à l’échelle de la machine. Ces étapes supposent que vous avez installé les fichiers ODAC 18.x à l’emplacement c:\oracle64 pour la version 64 bits et à l’emplacement c:\oracle32 pour la version 32 bits, et que la version du fichier Oracle.DataAccess.dll est 4.122.18.3. Pour inscrire le client ODP.NET managé, procédez comme suit :

### <a name="64-bit-power-bi-desktop"></a>Power BI Desktop 64 bits

1. Inscrivez le client non managé ODP.NET dans GAC :

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. Ajoutez les entrées du client non managé ODP.NET à machine.config :

   C:\oracle64\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3

### <a name="32-bit-power-bi-desktop"></a>Power BI Desktop 32 bits

1. Inscrivez le client non managé ODP.NET dans GAC :

   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:gac /providerpath:C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\Oracle.DataAccess.dll
2. Ajoutez les entrées du client non managé ODP.NET à machine.config :

   C:\oracle32\product\18.0.0\client_1\odp.net\bin\4\OraProvCfg.exe /action:config /force /product:odp /frameworkversion:v4.0.30319 /productversion:4.122.18.3
  
##  <a name="connection-string"></a><a name="Connection"></a> Chaîne de connexion  
 Contactez l'administrateur de votre base de données pour connaître les informations de connexion et d'identification à utiliser pour se connecter à la source de données. L'exemple de chaîne de connexion suivant spécifie une base de données Oracle sur le serveur nommé « Oracle18 » utilisant Unicode. Le nom du serveur doit correspondre à ce qui est défini dans le fichier de configuration Tnsnames.ora comme nom d'instance de serveur Oracle.  
  
```  
Data Source="Oracle"; Unicode="True"  
```  
  
 Pour obtenir d’autres exemples sur les chaînes de connexion, consultez [Créer des chaînes de connexion de données - Générateur de rapports et SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
##  <a name="credentials"></a><a name="Credentials"></a> Informations d'identification  
 Les informations d'identification sont obligatoires pour exécuter des requêtes, afficher l'aperçu du rapport localement et afficher l'aperçu du rapport à partir du serveur de rapports.  
  
 Après avoir publié votre rapport, vous pouvez devoir modifier les informations d'identification pour la source de données afin que les autorisations soient valides pour récupérer les données lorsque le rapport s'exécute sur le serveur de rapports.  
  
 Pour plus d’informations, consultez [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](specify-credential-and-connection-information-for-report-data-sources.md).  
  
  
##  <a name="queries"></a><a name="Query"></a> Requêtes  
 Pour créer un dataset, vous pouvez soit sélectionner une procédure stockée dans une liste déroulante, soit créer une requête SQL. Pour générer une requête, vous devez utiliser le concepteur de requêtes textuel. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes textuel &#40;Générateur de rapports&#41;](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md).  
  
 Vous pouvez spécifier des procédures stockées qui ne retournent qu'un seul jeu de résultats. L'utilisation des requêtes basées sur curseur n'est pas prise en charge.  
  
##  <a name="parameters"></a><a name="Parameters"></a> Paramètres  
 Si la requête inclut des variables de requête, les paramètres de rapport sont générés automatiquement. Les paramètres nommés sont pris en charge par cette extension. Pour Oracle version 9 ou une version ultérieure, les paramètres à valeurs multiples sont pris en charge.  
  
 Les paramètres de rapport sont créés avec des valeurs de propriétés par défaut que vous devrez peut-être modifier. Par exemple, chaque paramètre de rapport a le type de données **Texte**. Après avoir créé les paramètres de rapport, vous devrez peut-être modifier les valeurs par défaut. Pour plus d'informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> Notes  
 Avant de pouvoir connecter une source de données Oracle, l'administrateur système doit installer au préalable la version du fournisseur de données .NET pour Oracle qui prend en charge la récupération des données à partir de la base de données Oracle. Ce fournisseur de données doit être installé sur le même ordinateur que le Générateur de rapports, ainsi que sur le serveur de rapports.  
  
 Pour plus d’informations, consultez les articles suivants :  
  
-   [How to use Reporting Services to configure and to access an Oracle data source (en anglais)](/archive/blogs/dataaccesstechnologies/configure-oracle-data-source-for-sql-server-reporting-services-ssdt-and-report-server)  
-   [Comment ajouter des autorisations pour le principal de sécurité SERVICE RÉSEAU](https://support.microsoft.com/kb/870668)  
  
### <a name="alternate-data-extensions"></a>Autres extensions de données 
 
 Vous pouvez également récupérer des données à partir d'une base de données Oracle à l'aide d'un type de source de données OLE DB. Pour plus d’informations, consultez [Type de connexion OLE DB &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md).  

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions" 
### <a name="report-models"></a>Modèles de rapport  

 Vous pouvez également créer des modèles basés sur une base de données Oracle.  
::: moniker-end
   
### <a name="platform-and-version-information"></a>Informations sur les plateformes et les versions  

 Pour plus d’informations sur la prise en charge des plateformes et des versions, consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  

  
## <a name="see-also"></a>Voir aussi

 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
