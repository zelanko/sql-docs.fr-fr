---
title: Choisir une source de données (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 18b97b67590bfff4f01e5dff332722a3aba1cf7e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436876"
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>Choisir une source de données (Assistant Importation et Exportation SQL Server)
  Utilisez la page **choisir une source de données** pour spécifier la source des données que vous souhaitez copier.  
  
 Pour en savoir plus sur cet Assistant, consultez [Assistant Importation et Exportation SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant et sur les autorisations requises pour exécuter correctement l’Assistant, consultez [exécuter l’Assistant importation et exportation SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 **Source de données**  
 Permet de choisir le fournisseur de données qui correspond au format de stockage de la source. Plusieurs fournisseurs peuvent être disponibles pour votre source de données. Par exemple, avec, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous pouvez utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, le .NET Framework Fournisseur de données pour SQL Server ou le fournisseur Microsoft OLE DB pour SQL Server.  
  
 Le nombre d'options de la propriété **Source de données** varie en fonction des fournisseurs installés sur l'ordinateur. Les tableaux suivants répertorient les options de destinations fréquemment utilisées. Pour les autres fournisseurs, consultez la documentation du fournisseur.  
  
## <a name="dynamic-options"></a>Options dynamiques  
 Les paragraphes ci-dessous indiquent les options disponibles pour plusieurs sources de données. Toutes les sources de données disponibles dans la liste déroulante Source de données ne sont pas répertoriées ici.  
  
### <a name="data-source--sql-server-native-client-and-microsoft-ole-db-provider-for-sql-server"></a>Source de données = SQL Server Native Client et Fournisseur Microsoft OLE DB pour SQL Server  
 **Nom du serveur**  
 Tapez le nom du serveur qui contient les données ou choisissez un serveur dans la liste.  
  
 **Utiliser l'authentification Windows**  
 Spécifiez si le package doit utiliser l'authentification [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows pour la connexion à la base de données. L'authentification Windows est recommandée pour renforcer la sécurité.  
  
 **Utiliser l’authentification SQL Server**  
 Spécifiez si le package doit utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la connexion à la base de données. Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez fournir un nom d’utilisateur et un mot de passe.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur pour la connexion à la base de données lorsque vous utilisez l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Mot de passe**  
 Tapez le mot de passe pour la connexion à la base de données quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Sauvegarde de la base de données**  
 Sélectionnez dans la liste la base de données pour l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiée.  
  
 **Actualisation**  
 Cliquez sur **Actualiser** pour restaurer la liste des bases de données disponibles.  
  
### <a name="data-source--net-framework-data-provider-for-sql-server"></a>Source de données = fournisseur de données .NET Framework pour SQL Server  
 Cette page présente une liste alphabétique des options pour le fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les options les plus importantes sont présentées dans le tableau suivant.  
  
 **Source de données**  
 Tapez le nom du serveur qui contient les données ou choisissez un serveur dans la liste.  
  
 **Catalogue initial**  
 Tapez le nom de la base de données source.  
  
 **Sécurité intégrée**  
 Spécifiez `True` pour établir la connexion en utilisant l'authentification intégrée de Windows (recommandé) ou `False` pour établir la connexion en utilisant l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous spécifiez `False`, vous devez entrer un ID d'utilisateur et un mot de passe. La valeur par défaut est `False`.  
  
 **ID d'utilisateur**  
 Spécifiez un nom d'utilisateur pour la connexion à la base de données lorsque vous utilisez l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Mot de passe**  
 Tapez le mot de passe pour la connexion à la base de données quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les options supplémentaires fournies lorsque vous sélectionnez ce fournisseur ne sont pas indispensables pour la connexion à la base de données source [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour une description de ces options supplémentaires, consultez la documentation du fournisseur de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le Kit de développement logiciel (SDK) [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
### <a name="data-source--microsoft-excel"></a>Source de données = Microsoft Excel  
  
> [!NOTE]  
>  Sélectionnez **Microsoft Excel** uniquement si vous souhaitez vous connecter à une source de données qui utilise Excel 2003 ou une version antérieure. Pour vous connecter à une source de données qui utilise Excel 2007, sélectionnez **Microsoft Office 12,0 accès Moteur de base de données OLE DB fournisseur**, cliquez sur **Propriétés**, puis sous l’onglet **tous** de la boîte de dialogue **Propriétés des liaisons de données** , entrez `Excel 12.0` comme valeur pour les **propriétés étendues**.  
  
 **Chemin de fichier Excel**  
 Spécifiez le chemin d'accès et le nom de la feuille de calcul à partir de laquelle les données doivent être importées. Par exemple, **C:\MyData.xls, \\\Sales\Database\Northwind.xls**. Ou cliquez sur **Parcourir**.  
  
 **Parcourir**  
 Permet de rechercher la feuille de calcul à l’aide de la boîte de dialogue **Ouvrir**.  
  
 **Version d’Excel**  
 Sélectionnez la version d'Excel dans laquelle les données source sont enregistrées.  
  
> [!NOTE]  
>  Lorsque vous importez des données à partir d'une source [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)], l'Assistant utilise le composant de source Excel [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Pour plus d'informations sur les considérations relatives à l'utilisation et sur les problèmes connus, consultez [Excel Source](../data-flow/excel-source.md).  
  
### <a name="data-source--microsoft-access"></a>Source de données = Microsoft Access  
  
> [!NOTE]  
>  Sélectionnez **Microsoft Access** uniquement si vous souhaitez vous connecter à une base de données qui utilise Access 2003 ou une version antérieure. Pour vous connecter à une base de données qui utilise Access 2007, sélectionnez **Microsoft Office 12,0 accès Moteur de base de données OLE DB fournisseur à** la place.  
  
 **Nom de fichier**  
 Spécifiez le chemin d'accès et le nom du fichier de base de données à partir duquel les données doivent être importées. Par exemple, **C:\MyData.mdb, \\\Sales\Database\Northwind.mdb**. Ou cliquez sur **Parcourir**.  
  
 **Parcourir**  
 Permet de rechercher le fichier de la base de données à l’aide de la boîte de dialogue **Ouvrir**.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur valide pour la connexion à la base de données lorsqu'un fichier d'informations d'un groupe de travail est associé à la base de données.  
  
 **Mot de passe**  
 Fournissez le mot de passe utilisateur pour la connexion à la base de données lorsqu'un fichier d'informations d'un groupe de travail est associé à la base de données. Cependant, si la base de données est protégée par un seul mot de passe pour tous les utilisateurs, vous devez fournir cette valeur dans la boîte de dialogue **Propriétés des liaisons de données** accessible en cliquant sur **Avancé**.  
  
 **Avancé**  
 Vous pouvez spécifier des options avancées, telles que le mot de passe de la base de données ou un fichier d’informations de groupe de travail autre que celui par défaut, à l’aide de la boîte de dialogue **Propriétés des liaisons de données** . Pour plus d’informations sur les propriétés du fournisseur OLE DB, recherchez dans la section accès aux données de [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).  
  
### <a name="data-source--flat-file-source"></a>Source de données = Source de fichier plat  
 Consultez les rubriques suivantes pour obtenir des informations sur les options d'une source de données dans un fichier plat.  
  
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../flat-file-connection-manager-editor-columns-page.md)  
  
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Avancé&#41;](../flat-file-connection-manager-editor-advanced-page.md)  
  
 [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../flat-file-connection-manager-editor-preview-page.md)  
  
  
