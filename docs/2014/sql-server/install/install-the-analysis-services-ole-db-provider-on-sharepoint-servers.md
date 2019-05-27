---
title: Installer le fournisseur Analysis Services OLE DB sur les serveurs SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2c62daf9-1f2d-4508-a497-af62360ee859
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 39f875041963cc8d48b2dcf70515c99042cdb8fb
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66094435"
---
# <a name="install-the-analysis-services-ole-db-provider-on-sharepoint-servers"></a>Installer le fournisseur OLE DB Analysis Services sur les serveurs SharePoint
  Le fournisseur Microsoft OLE DB pour Analysis Services (MSOLAP) est une interface que les applications clientes utilisent pour interagir avec les données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Dans un environnement SharePoint qui inclut [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], le fournisseur gère les demandes de connexion aux données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 Le fournisseur de données est inclus dans le package d'installation de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] (spPowerPivot.msi), mais peut nécessiter une installation manuelle. Il existe deux raisons pour lesquelles vous devrez peut-être installer manuellement un bibliothèque cliente ou un fournisseur de données sur un serveur SharePoint.  
  
-   **Activer la compatibilité descendante**. Les classeurs [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] spécifient la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] du fournisseur OLE DB Analysis Services dans leur chaîne de connexion. En conséquence, cette version du fournisseur doit être présente sur l'ordinateur pour la réussite de la requête.  
  
-   **Activer l’accès aux données sur une instance d’Excel Services dédiée**. Si votre batterie de serveurs SharePoint inclut Excel Services sur un serveur qui ne dispose pas de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], installez la version [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] du fournisseur et d'autres composants de connectivité clients à l'aide du package d'installation [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].  
  
    > [!NOTE]  
    >  Ces scénarios ne sont pas mutuellement exclusifs. L'hébergement de plusieurs versions de classeur dans une batterie de serveurs qui inclut des serveurs d'applications exécutant Excel Services sans une instance de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] nécessite que vous installiez la version antérieure et la dernière version du fournisseur de données sur chaque ordinateur Excel Services.  
  
  
##  <a name="bkmk_vers"></a> Versions du fournisseur OLE DB prenant en charge les accès aux données PowerPivot  
 Une batterie de serveurs SharePoint peut inclure plusieurs versions du fournisseur OLE DB Analysis Services, notamment des versions antérieures qui ne prennent pas en charge l'accès aux données PowerPivot.  
  
 Par défaut, SharePoint 2010 installe la version [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] du fournisseur. Bien qu'elle soit identifiée comme version MSOLAP.4 (même numéro de version que pour [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), cette version ne fonctionne pas pour l'accès aux données PowerPivot. Pour établir des connexions avec succès, vous devez disposer de la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du fournisseur.  
  
 Une version postérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] du fournisseur OLE DB comprend la prise en charge du transport et de la connexion pour les structures de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. Les classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] utilisent des versions plus récentes de ce fournisseur pour demander le traitement de requêtes par des serveurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la batterie. Pour obtenir une version mise à jour, vous pouvez la télécharger et l'installer via une page SQL Server Feature Pack.  
  
 Le tableau suivant décrit les versions valides :  
  
|Version du produit|Version de fichier|Valide pour :|  
|---------------------|------------------|----------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|MSOLAP100.dll dans le système de fichiers<br /><br /> MSOLAP.4 dans une chaîne de connexion Excel<br /><br /> Détails de la version de fichier 10.50.1600 ou version ultérieure|Utilisée pour les modèles de données créés à l'aide de la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] de PowerPivot pour Excel.|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|MSOLAP110.dll dans le système de fichiers<br /><br /> MSOLAP.5 dans une chaîne de connexion Excel<br /><br /> Détails de la version de fichier 11.0.0000 ou version ultérieure|Utilisée pour les modèles de données créés à l'aide de la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] our [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour Excel.|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|MSOLAP120.dll dans le système de fichiers<br /><br /> Détails de la version de fichier 12.0.20000 ou version ultérieure|Utilisée pour les modèles de données autres que les modèles [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].|  
  
  
##  <a name="bkmk_why"></a> Pourquoi vous devez installer le fournisseur OLE DB  
 Il existe deux scénarios qui nécessitent l'installation manuelle du fournisseur OLE DB sur les serveurs de la batterie.  
  
 **Le scénario le plus courant** est lorsque vous disposez plus anciennes et les versions plus récentes de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] classeurs sont enregistrés dans les bibliothèques dans la batterie de serveurs de documents. Si les analystes de votre entreprise utilisent la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour Excel et qu'ils enregistrent ces classeurs dans une installation de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], le classeur plus ancien ne fonctionne pas. Sa chaîne de connexion fait référence à une version antérieure du fournisseur, qui ne sera pas sur le serveur, sauf si vous l’installez. L'installation de ces deux versions activera l'accès aux données pour les classeurs PowerPivot créés dans des versions plus anciennes et plus récentes de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour Excel. Le programme d'installation de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] n'installe pas la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] du fournisseur. Vous devez donc l'installer manuellement si vous utilisez des classeurs provenant d'une version antérieure.  
  
 **Le deuxième scénario** est lorsque vous avez un serveur dans une batterie de serveurs SharePoint qui exécute Excel Services, mais pas [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Dans ce cas, le serveur d'applications qui exécute Excel Services doit être mis à jour manuellement pour utiliser une version plus récente du fournisseur. Cela est nécessaire pour se connecter à une instance de PowerPivot pour SharePoint. Si Excel Services utilise une version antérieure du fournisseur, la demande de connexion échoue. Notez que le fournisseur doit être installé à l'aide du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou du package d'installation de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] (spPowerPivot.msi) afin de vous assurer que tous les composants nécessaires pour prendre en charge [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sont installés.  
  
  
##  <a name="bkmk_sql11"></a> Installer le fournisseur OLE DB SQL Server 2012 sur un serveur Excel Services à l’aide du programme d’installation de SQL Server  
 Utilisez les instructions suivantes pour ajouter le fournisseur OLE DB et d'autres composants de connectivité clients aux serveurs SharePoint sur lesquels ils ne sont pas encore installés, comme les serveurs d'applications qui exécutent Excel Services sans PowerPivot pour SharePoint sur le même matériel.  
  
 Utilisez ces instructions pour installer le fournisseur OLE DB pour Analysis Services actuel et ajouter la **Microsoft.AnalysisServices.Xmla.dll** à l’assembly global.  
  
#### <a name="run-sql-server-setup-and-install-the-client-connectivity-tools"></a>Exécuter le programme d'installation de SQL Server et installer les outils de connectivité clients  
  
1.  Sur le serveur d'applications qui héberge Excel Services, exécutez le programme d'installation de SQL Server.  
  
2.  Dans la page d’Installation, choisissez **nouvelle installation SQL Server autonome ou ajout de fonctionnalités à une installation existante**.  
  
3.  Dans la page Type d’Installation, choisissez **effectuer une nouvelle installation de SQL Server 2012**.  
  
4.  Dans la page rôle d’installation, choisissez **Installation de fonctionnalités SQL Server**.  
  
5.  Sur le **sélection des fonctionnalités** , cliquez sur **connectivité des outils clients**. Cette option installe **Microsoft.AnalysisServices.Xmla.dll**  
  
     Ne sélectionnez pas d'autres composants.  
  
6.  Cliquez sur **suivant** pour terminer l’Assistant, puis cliquez sur **installer** pour exécuter le programme d’installation.  
  
7.  Répétez les étapes précédentes si vous disposez d'autres serveurs exécutant Excel Services sans que PowerPivot pour SharePoint soit installé sur le même serveur.  
  
#### <a name="verify-msolap5-is-a-trusted-provider"></a>Vérifiez que MSOLAP.5 est un fournisseur approuvé.  
  
1.  Dans l'administration centrale, cliquez sur **Gérer les applications de service**, puis cliquez sur l'application de service Excel Services.  
  
2.  Cliquez sur **Fournisseurs de données approuvés**.  
  
3.  Vérifiez que MSOLAP.5 figure dans la liste. Selon la manière dont vous avez configuré PowerPivot pour SharePoint, MSOLAP.5 peut être déjà approuvé. Si vous avez utilisé l'outil de configuration PowerPivot mais en excluant ensuite cette action de la liste des tâches, MSOLAP.5 n'est pas approuvé par Excel Services et doit être ajouté manuellement.  
  
4.  Si MSOLAP n’est pas répertorié, cliquez sur **ajouter un fournisseur de données approuvé**.  
  
5.  Pour l’ID du fournisseur, tapez `MSOLAP.5`.  
  
6.  Pour le type de fournisseur, vérifiez que OLE DB est sélectionné.  
  
7.  Dans la description du fournisseur, tapez **Fournisseur Microsoft OLE DB pour OLAP Services 11.0**.  
  
#### <a name="verify-installation"></a>Vérifier l'installation  
  
1.  Accédez au dossier Program files\Microsoft Analysis Services\AS OLEDB\110.  
  
2.  Cliquez avec le bouton droit sur msolap110.dll, puis sélectionnez **Propriétés**.  
  
3.  Cliquez sur **Détails**.  
  
4.  Consultez les informations de version du fichier. La version doit inclure 11.00. \<buildnumber >.  
  
5.  Dans le dossier Windows\assembly, vérifiez les Microsoft.AnalysisServices.Xmla.dll, version 11.0.0.0, est répertorié.  
  
  
##  <a name="bkmk_install2012_from_sppowerpivot_msi"></a> Utiliser le PowerPivot pour le package d’Installation de SharePoint (spPowerPivot.msi) pour installer le fournisseur OLE DB SQL Server 2012  
 Installer le [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] fournisseur OLE DB sur et serveur Excel Services à l’aide de la [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] package d’installation **(spPowerPivot.msi)**.  
  
#### <a name="download-the-msolap5-provider-from-the-includesssql11sp1includessssql11sp1-mdmd-feature-pack"></a>Téléchargez le fournisseur MSOLAP.5 à partir du Feature Pack [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] .  
  
1.  Accédez à [Microsoft® SQL Server® 2012 SP1 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35580)  
  
2.  Cliquez sur **Instructions d’installation**.  
  
3.  Consultez la section « Microsoft Analysis Services OLE DB fournisseur pour Microsoft SQL Server 2012 SP1 ». Téléchargez le fichier et démarrez l'installation.  
  
4.  Sur le **sélection des fonctionnalités** page, sélectionnez **fournisseur Analysis Services OLE DB pour SQL Server**. Désélectionnez les autres composants et finalisez l'installation. Pour plus d’informations sur le fichier spPowerPivot.msi, consultez [installer ou désinstaller le PowerPivot pour SharePoint Add-in &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  
  
5.  Inscrivez MSOLAP.5 en tant que fournisseur approuvé dans SharePoint Excel Services. Pour plus d'informations, consultez [Ajouter MSOLAP.5 en tant que fournisseur de données approuvé dans Excel Services](https://technet.microsoft.com/library/hh758436.aspx).  
  
  
##  <a name="bkmk_kj"></a> Installer le fournisseur SQL Server 2008 R2 OLE DB pour héberger précédemment classeurs de version  
 Suivez les instructions suivantes pour installer la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] du fournisseur MSOLAP.4 et inscrire le fichier Microsoft.AnalysisServices.ChannelTransport.dll. ChannelTransport est un sous-composant du fournisseur OLE DB Analysis Services. La version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] du fournisseur lit le Registre lors de l'utilisation de ChannelTransport pour établir une connexion. L'inscription de ce fichier est une étape postérieure à l'installation requise uniquement pour les connexions gérées par le fournisseur [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] sur un serveur [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
#### <a name="step-1-download-and-install-the-client-library"></a>Étape 1 : Télécharger et installer la bibliothèque cliente  
  
1.  Sur le [page SQL Server 2008 R2 Feature Pack](https://go.microsoft.com/fwlink/?LinkId=159570), recherchez le fournisseur OLE DB Microsoft Analysis Services pour Microsoft SQL Server 2008 R2.  
  
2.  Téléchargez le package x64 du programme d'installation `SQLServer2008_ASOLEDB10.msi`. Bien que le nom de fichier contienne SQLServer2008, il s'agit du fichier approprié pour la version SQL Server 2008 R2 du fournisseur.  
  
3.  Sur l'ordinateur qui dispose d'une installation de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], exécutez le fichier .msi pour installer la bibliothèque.  
  
4.  Si d'autres serveurs de la batterie de serveurs exécutent uniquement Excel Services, sans [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] sur le même serveur, répétez les étapes précédentes afin d'installer la version 2008 R2 du fournisseur sur l'ordinateur Excel Services.  
  
#### <a name="step-2-register-the-microsoftanalysisserviceschanneltransportdll-file"></a>Étape 2 : Inscrire le fichier Microsoft.AnalysisServices.ChannelTransport.dll  
  
1.  Servez-vous de l'utilitaire regasm.exe pour inscrire le fichier. Si vous n’avez pas exécuté regasm.exe, ajoutez son dossier parent, C:\Windows\Microsoft.NET\Framework64\v4.0.30319\\, à la variable système path.  
  
2.  Ouvrez une invite de commandes avec des autorisations d'administrateur.  
  
3.  Accédez au dossier C:\Windows\assembly\GAC_MSIL\Microsoft.AnalysisServices.ChannelTransport\10.0.0.0__89845dcd8080cc91  
  
4.  Entrez la commande suivante : `regasm microsoft.analysisservices.channeltransport.dll`  
  
5.  Répétez les étapes précédentes pour tous les ordinateurs sur lesquels vous avez installé manuellement la version 2008 R2 du fournisseur.  
  
#### <a name="verify-installation"></a>Vérifier l'installation  
  
1.  Vous devez maintenant être en mesure de découper ou de filtrer des classeurs [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Si une erreur se produit, vérifiez que vous avez utilisé la version 64 bits de regasm.exe pour inscrire le fichier.  
  
2.  En outre, vous pouvez vérifier la version du fichier.  
  
     Atteindre `C:\Program files\Microsoft Analysis Services\AS OLEDB\10`. Avec le bouton droit **msolap100.dll** et sélectionnez **propriétés**. Cliquez sur **Détails**.  
  
     Consultez les informations de version du fichier. La version doit inclure 10.50. \<buildnumber >.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
