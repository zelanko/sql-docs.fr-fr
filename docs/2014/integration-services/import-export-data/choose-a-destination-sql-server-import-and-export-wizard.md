---
title: Choisir une destination (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.chooseadestination.f1
ms.assetid: 1898be15-3e69-42d3-8ecb-3733c9f6c8e3
caps.latest.revision: 54
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 75a9ef3ae1c496c2469ea27d766eedf317af5bf2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176156"
---
# <a name="choose-a-destination-sql-server-import-and-export-wizard"></a>Choisir une destination (Assistant Importation et Exportation SQL Server)
  Utilisez le **choisir une Destination** page pour spécifier la destination des données que vous souhaitez copier.  
  
 Pour en savoir plus sur cet Assistant, consultez [SQL Server Assistant Importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant, ainsi que les autorisations requises pour exécuter l’Assistant avec succès, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 L’objectif de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation consiste à copier des données à partir d’une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="static-options"></a>Options statiques  
 **Destination**  
 Permet de choisir le fournisseur de données qui correspond au format de stockage de données de la destination. Plusieurs fournisseurs peuvent être disponibles pour votre source de données. Par exemple, avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous pouvez utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, le fournisseur de données .NET Framework pour SQL Server ou le fournisseur Microsoft OLE DB pour SQL Server.  
  
> [!NOTE]  
>  Pour enregistrer des données sur une destination ODBC, sélectionnez le fournisseur de données .NET Framework pour ODBC.  
  
 Le **Source de données** propriété a un nombre variable d’options qui varient selon les fournisseurs installés sur l’ordinateur. Les tableaux suivants répertorient les options pour quelques destinations fréquentes. Pour les autres fournisseurs, consultez la documentation du fournisseur.  
  
## <a name="dynamic-options"></a>Options dynamiques  
 Les paragraphes ci-dessous indiquent les options disponibles pour plusieurs sources de données. Toutes les destinations disponibles dans la liste déroulante Destination ne figurent pas dans cette liste.  
  
### <a name="destination--sql-server-native-client-or-microsoft-ole-db-provider-for-sql-server"></a>Destination = SQL Server Native Client ou fournisseur Microsoft OLE DB pour SQL Server  
 **Nom du serveur**  
 Tapez le nom du serveur qui doit recevoir les données ou choisissez un serveur dans la liste.  
  
 **Utiliser l'authentification Windows**  
 Spécifiez si le package doit utiliser l'authentification Microsoft Windows pour la connexion à la base de données. L'authentification Windows est recommandée pour renforcer la sécurité.  
  
 **Utiliser l’authentification SQL Server**  
 Spécifiez si le package doit utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification pour vous connecter à la base de données. Si vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez fournir un nom d’utilisateur et un mot de passe.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d’utilisateur pour la connexion de base de données lorsque vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.  
  
 **Mot de passe**  
 Tapez le mot de passe pour la connexion à la base de données quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Sauvegarde de la base de données**  
 Sélectionnez dans la liste des bases de données sur l’instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou créez une nouvelle base de données en cliquant sur **New**.  
  
 **Actualiser**  
 Cliquez sur **Actualiser** pour restaurer la liste des bases de données disponibles.  
  
 **Nouveau**  
 Créer une nouvelle base de données de destination à l’aide de la **Create Database** boîte de dialogue.  
  
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
  
|Valeur|Description|  
|-----------|-----------------|  
|Délimité|Les colonnes sont séparées par un délimiteur spécifié à la page **Colonnes** .|  
|Largeur fixe|Les colonnes ont une largeur fixe.|  
|En drapeau à droite|Dans les fichiers en drapeau à droite, chaque colonne a une largeur fixe, sauf la dernière qui est délimitée par le séparateur de lignes.|  
  
 **Identificateur de texte**  
 Tapez le qualificateur de texte à utiliser. Par exemple, vous pouvez indiquer que chaque colonne de texte doit être entourée de guillemets.  
  
 **Noms de colonne dans la première ligne de données**  
 Indiquez si vous souhaitez afficher les noms de colonne dans la première ligne de données.  
  
### <a name="destination--microsoft-excel"></a>Destination = Microsoft Excel  
  
> [!NOTE]  
>  Sélectionnez **Microsoft Excel** uniquement si vous souhaitez vous connecter à une source de données qui utilise Excel 2003 ou une version antérieure. Pour vous connecter à une source de données qui utilise Excel 2007, sélectionnez **Microsoft Office 12.0 Access Database Engine fournisseur OLE DB**, cliquez sur **propriétés**, puis, dans le **tous les** onglet de la **Propriétés des liaisons de données** boîte de dialogue pour **propriétés étendues**, entrez `Excel 12.0`.  
  
 **Chemin de fichier Excel**  
 Spécifiez le chemin d’accès et le nom pour le classeur dans lequel stocker les données (par exemple, C:\MyData.xls, \\\Sales\Database\Northwind.xls). Ou cliquez sur **Parcourir** pour localiser un classeur.  
  
 **Parcourir**  
 Recherchez un classeur Excel à l’aide de la **Open** boîte de dialogue.  
  
 **Version Excel**  
 Permet de sélectionner la version d'Excel utilisée par le classeur de destination.  
  
> [!NOTE]  
>  Lorsque vous exportez des données à un [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] destination, l’Assistant utilise le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] composant de Destination Excel. Pour plus d’informations sur certaines considérations sur l’utilisation et les problèmes connus, consultez [Destination Excel](../data-flow/excel-destination.md).  
  
### <a name="destination--microsoft-access"></a>Destination = Microsoft Access  
  
> [!NOTE]  
>  Sélectionnez **Microsoft Access** uniquement si vous souhaitez vous connecter à une base de données qui utilise Access 2003 ou une version antérieure. Pour vous connecter à une base de données qui utilise Access 2007, sélectionnez **Microsoft Office 12.0 Access Database Engine fournisseur OLE DB**.  
  
 **Nom de fichier**  
 Spécifiez le chemin d’accès et le nom du fichier de base de données dans lequel stocker les données (par exemple, C:\MyData.mdb, \\\Sales\Database\Northwind.mdb). Ou cliquez sur **Parcourir** pour localiser un fichier de base de données.  
  
 **Parcourir**  
 Recherchez le fichier de base de données à l’aide de la **Open** boîte de dialogue.  
  
 **Nom d'utilisateur**  
 Spécifiez un nom d'utilisateur valide pour la connexion à la base de données lorsqu'un fichier d'informations d'un groupe de travail est associé à la base de données.  
  
 **Mot de passe**  
 Fournissez le mot de passe utilisateur pour la connexion à la base de données lorsqu'un fichier d'informations d'un groupe de travail est associé à la base de données. Cependant, si la base de données est protégée par un seul mot de passe pour tous les utilisateurs, vous devez indiquer cette valeur dans la boîte de dialogue **Propriétés des liaisons de données** , à laquelle vous pouvez accéder à l'aide du bouton **Avancé** .  
  
 **Avancé**  
 Permet de spécifier les options avancées, telles que le mot de passe de la base de données ou un autre fichier d’informations de groupe de travail que celui défini par défaut, à l’aide de la boîte de dialogue **Propriétés des liaisons de données**. Pour plus d'informations sur les propriétés du fournisseur OLE DB, effectuez une recherche dans la section « Data Access » (en anglais) de [MSDN Library](http://go.microsoft.com/fwlink/?linkid=62553).  
  
  
