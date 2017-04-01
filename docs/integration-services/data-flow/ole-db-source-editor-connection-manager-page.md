---
title: "&#201;diteur de source OLE DB (page Gestionnaire de connexions) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.oledbsourceadapter.connection.f1"
helpviewer_keywords: 
  - "Éditeur de source OLE DB"
ms.assetid: 53699902-8699-4547-b56b-a5b2079e98b6
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# &#201;diteur de source OLE DB (page Gestionnaire de connexions)
  La page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source OLE DB** vous permet de sélectionner le gestionnaire de connexions OLE DB pour la source. Cette page vous permet également de sélectionner une table ou une vue à partir de la base de données.  
  
> [!NOTE]  
>  Pour charger des données à partir d’une source de données qui utilise [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007, utilisez une source OLE DB. Vous ne pouvez pas utiliser une source Excel pour charger des données à partir d'une source de données Excel 2007. Pour plus d’informations, consultez [Configurer le gestionnaire de connexions OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md).  
>   
>  Pour charger des données à partir d'une source de données qui utilise [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2003 ou une version antérieure, utilisez une source Excel. Pour plus d’informations, consultez [Éditeur de source Excel &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/excel-source-editor-connection-manager-page.md).  
  
> [!NOTE]  
>  La propriété **CommandTimeout** de la source OLE DB n’est pas disponible dans **l’Éditeur de source OLE DB**, mais peut être définie à l’aide de **l’Éditeur avancé**. Pour plus d’informations sur cette propriété, consultez la section sur la source Excel dans [Propriétés personnalisées OLE DB](../../integration-services/data-flow/ole-db-custom-properties.md).  
  
 Pour en savoir plus sur la source OLE DB, consultez [Source OLE DB](../../integration-services/data-flow/ole-db-source.md).  
  
## Ouvrir l'Éditeur de source OLE (page Gestionnaire de connexions)  
  
1.  Ajoutez la source OLE DB au package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur le composant de la source, puis cliquez sur **Modifier**.  
  
3.  Cliquez sur **Gestionnaire de connexions**.  
  
## Options statiques  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB**.  
  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Option|Description|  
|------------|-----------------|  
|Table ou vue|Permet de récupérer les données d'une table ou d'une vue dans la source de données OLE DB.|  
|Variable de nom de table ou de vue|Spécifiez le nom de la table ou de la vue dans une variable.<br /><br /> **Informations connexes :** [Utiliser des variables dans des packages](../Topic/Use%20Variables%20in%20Packages.md)|  
|Commande SQL|Récupérez les données de la source de données OLE DB à l'aide d'une requête SQL.|  
|Commande SQL à partir d'une variable|Spécifiez le texte de la requête SQL dans une variable.|  
  
 **Aperçu**  
 Affichez un aperçu des résultats via la boîte de dialogue **Vue de données**. Le mode **Aperçu** peut afficher jusqu’à 200 lignes.  
  
> [!NOTE]  
>  Lorsque vous affichez l'aperçu des données, les colonnes ayant un type CLR défini par l'utilisateur ne contiennent pas de données. Les valeurs \<valeur trop grande pour être affichée> ou System.Byte[] s’affichent à la place. La première s’affiche lorsque le fournisseur SQL OLE DB accède à la source de données, la seconde lorsque vous utilisez le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## Options dynamiques du mode d'accès aux données  
  
### Mode d'accès aux données = Table ou vue  
 **Nom de la table ou de la vue**  
 Sélectionnez le nom de la table ou de la vue dans la liste de celles qui sont disponibles dans la source de données.  
  
### Mode d'accès aux données = Variable de nom de table ou de vue  
 **Nom de la variable**  
 Sélectionnez la variable qui contient le nom de la table ou de la vue.  
  
### Mode d'accès aux données = Commande SQL  
 **Texte de la commande SQL**  
 Entrez le texte d'une requête SQL, générez la requête en cliquant sur **Générer une requête** ou recherchez le fichier qui contient le texte de la requête en cliquant sur **Parcourir**.  
  
 **Paramètres**  
 Si vous avez entré une requête paramétrable en spécifiant ? comme espace réservé de paramètre dans le texte de la requête, utilisez la boîte de dialogue **Définition des paramètres de la requête** pour mapper des paramètres d’entrée de la requête à des variables du package.  
  
 **Construire une requête**  
 Utilisez la boîte de dialogue **Générateur de requêtes** pour construire la requête SQL visuellement.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir**, localisez le fichier contenant le texte de la requête SQL.  
  
 **Analyser la requête**  
 Vérifiez la syntaxe du texte de la requête.  
  
### Mode d'accès aux données = Commande SQL à partir d'une variable  
 **Nom de la variable**  
 Sélectionnez la variable qui contient le texte de la requête SQL.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de source OLE DB &#40;page Colonnes&#41;](../../integration-services/data-flow/ole-db-source-editor-columns-page.md)   
 [Éditeur de source OLE DB &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/ole-db-source-editor-error-output-page.md)   
 [Extraire des données à l'aide de la source OLE DB](../../integration-services/data-flow/extract-data-by-using-the-ole-db-source.md)   
 [Gestionnaire de connexions OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)  
  
  