---
title: Choisir une destination (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 50c9419911f83c98fba5baf0f995ffbeafb916ad
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965649"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>Choisir une destination (Assistant Importation et Exportation SQL Server)
  Utilisez la page **choisir une destination** pour spécifier la destination des données que vous souhaitez copier.  
  
 Pour en savoir plus sur cet Assistant, consultez [Assistant Importation et Exportation SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que sur les autorisations requises pour exécuter correctement l’Assistant, consultez [exécuter l’Assistant importation et exportation SQL Server](start-the-sql-server-import-and-export-wizard.md).  
  
 La fonction de l'Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est de copier des données d'une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Options statiques  
 **Destination**  
 Permet de choisir le fournisseur de données qui correspond au format de stockage de données de la destination. Plusieurs fournisseurs peuvent être disponibles pour votre source de données. Par exemple, avec, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous pouvez utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, le .NET Framework Fournisseur de données pour SQL Server ou le fournisseur Microsoft OLE DB pour SQL Server.  
  
> [!NOTE]  
>  Pour enregistrer des données sur une destination ODBC, sélectionnez le fournisseur de données .NET Framework pour ODBC.  
  
 La propriété de la **source de données** a un nombre variable d’options, qui varient en fonction des fournisseurs installés sur l’ordinateur. Les tableaux suivants répertorient les options pour quelques destinations fréquentes. Pour les autres fournisseurs, consultez la documentation du fournisseur.  
  
## <a name="dynamic-options"></a>Options dynamiques  
 Les paragraphes ci-dessous indiquent les options disponibles pour plusieurs sources de données. Toutes les destinations disponibles dans la liste déroulante Destination ne figurent pas dans cette liste.  
  
### <a name="destination--sql-server-native-client-or-microsoft-ole-db-provider-for-sql-server"></a>Destination = SQL Server Native Client ou fournisseur Microsoft OLE DB pour SQL Server  
 **Nom du serveur**  
 Tapez le nom du serveur qui doit recevoir les données ou choisissez un serveur dans la liste.  
  
 **Utiliser l'authentification Windows**  
 Spécifiez si le package doit utiliser l'authentification Microsoft Windows pour la connexion à la base de données. L'authentification Windows est recommandée pour renforcer la sécurité.  
  
 **Utiliser l’authentification SQL Server**  
 Spécifiez si le package doit utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la connexion à la base de données. Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez fournir un nom d’utilisateur et un mot de passe.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur pour la connexion à la base de données lorsque vous utilisez l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Mot de passe**  
 Tapez le mot de passe pour la connexion à la base de données quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Sauvegarde de la base de données**  
 Sélectionnez dans la liste des bases de données sur l’instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou créez une nouvelle base de données en cliquant sur **nouveau**.  
  
 **Actualisation**  
 Cliquez sur **Actualiser** pour restaurer la liste des bases de données disponibles.  
  
 **Nouveau**  
 Créez une nouvelle base de données de destination à l’aide de la boîte **de dialogue créer une base de données** .  
  
### <a name="destination--flat-file-destination"></a>Destination = destination de fichier plat  
 **Nom de fichier**  
 Spécifiez le chemin d'accès et le nom du fichier dans lequel les données doivent être stockées. Ou cliquez sur **Parcourir** pour localiser un fichier.  
  
 **Parcourir**  
 Permet de rechercher un fichier à l’aide de la boîte de dialogue **Ouvrir**.  
  
 **Paramètres régionaux**  
 Permet de spécifier l'ID des paramètres régionaux (LCID, locale ID) qui définit l'ordre de tri des caractères et la mise en forme de la date et de l'heure.  
  
 **Unicode**  
 Indique s'il convient d'utiliser Unicode. Dans l'affirmative, il n'est pas nécessaire de spécifier une page de codes.  
  
 **Page de codes**  
 Permet de spécifier la page de codes correspondant à la langue à utiliser.  
  
 **Format**  
 Permet de préciser la mise en forme à utiliser : délimitée, à largeur fixe ou en drapeau à droite.  
  
|Value|Description|  
|-----------|-----------------|  
|Delimited|Les colonnes sont séparées par un délimiteur spécifié à la page **Colonnes** .|  
|Largeur fixe|Les colonnes ont une largeur fixe.|  
|En drapeau à droite|Dans les fichiers en drapeau à droite, chaque colonne a une largeur fixe, sauf la dernière qui est délimitée par le séparateur de lignes.|  
  
 **Qualificateur de texte**  
 Tapez le qualificateur de texte à utiliser. Par exemple, vous pouvez indiquer que chaque colonne de texte doit être entourée de guillemets.  
  
 **Noms de colonne dans la première ligne de données**  
 Indiquez si vous souhaitez afficher les noms de colonne dans la première ligne de données.  
  
### <a name="destination--microsoft-excel"></a>Destination = Microsoft Excel  
  
> [!NOTE]  
>  Sélectionnez **Microsoft Excel** uniquement si vous souhaitez vous connecter à une source de données qui utilise Excel 2003 ou une version antérieure. Pour vous connecter à une source de données qui utilise Excel 2007, sélectionnez **Microsoft Office 12,0 accès Moteur de base de données OLE DB fournisseur**, cliquez sur **Propriétés**, puis sous l’onglet **tous** de la boîte de dialogue **Propriétés des liaisons de données** , pour **propriétés étendues**, entrez `Excel 12.0` .  
  
 **Chemin de fichier Excel**  
 Spécifiez le chemin d’accès et le nom de fichier du classeur dans lequel stocker les données (par exemple, C:\MyData.xls, \\\Sales\Database\Northwind.xls). Ou cliquez sur **Parcourir** pour localiser un classeur.  
  
 **Parcourir**  
 Localisez un classeur Excel à l’aide de la boîte de dialogue **ouvrir** .  
  
 **Version d’Excel**  
 Permet de sélectionner la version d'Excel utilisée par le classeur de destination.  
  
> [!NOTE]  
>  Lorsque vous exportez des données vers une destination [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] , l'Assistant utilise le composant de destination Excel [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour plus d’informations sur certaines considérations d’utilisation et les problèmes connus, consultez [destination Excel](../data-flow/excel-destination.md).  
  
### <a name="destination--microsoft-access"></a>Destination = Microsoft Access  
  
> [!NOTE]  
>  Sélectionnez **Microsoft Access** uniquement si vous souhaitez vous connecter à une base de données qui utilise Access 2003 ou une version antérieure. Pour vous connecter à une base de données qui utilise Access 2007, sélectionnez **Microsoft Office 12,0 accès Moteur de base de données OLE DB fournisseur**.  
  
 **Nom de fichier**  
 Spécifiez le chemin d’accès et le nom du fichier de base de données dans lequel stocker les données (par exemple, C:\MyData.mdb, \\ \Sales\Database\Northwind.mdb). Ou cliquez sur **Parcourir** pour localiser un fichier de base de données.  
  
 **Parcourir**  
 Accédez au fichier de base de données à l’aide de la boîte de dialogue **ouvrir** .  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur valide pour la connexion à la base de données lorsqu'un fichier d'informations d'un groupe de travail est associé à la base de données.  
  
 **Mot de passe**  
 Fournissez le mot de passe utilisateur pour la connexion à la base de données lorsqu'un fichier d'informations d'un groupe de travail est associé à la base de données. Cependant, si la base de données est protégée par un seul mot de passe pour tous les utilisateurs, vous devez indiquer cette valeur dans la boîte de dialogue **Propriétés des liaisons de données** , à laquelle vous pouvez accéder à l'aide du bouton **Avancé** .  
  
 **Avancé**  
 Permet de spécifier les options avancées, telles que le mot de passe de la base de données ou un autre fichier d’informations de groupe de travail que celui défini par défaut, à l’aide de la boîte de dialogue **Propriétés des liaisons de données**. Pour plus d'informations sur les propriétés du fournisseur OLE DB, effectuez une recherche dans la section « Data Access » (en anglais) de [MSDN Library](https://go.microsoft.com/fwlink/?linkid=62553).  
  
  
