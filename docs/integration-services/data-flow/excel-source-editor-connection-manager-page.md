---
title: "&#201;diteur de source Excel (page Gestionnaire de connexions) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.excelsourceadapter.connection.f1"
helpviewer_keywords: 
  - "Éditeur de source Excel"
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
caps.latest.revision: 39
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 39
---
# &#201;diteur de source Excel (page Gestionnaire de connexions)
  Le nœud **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source Excel** vous permet de sélectionner le classeur [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] de la source à utiliser. La source Excel lit les données à partir d'une feuille de calcul ou d'une plage nommée dans un classeur existant.  
  
> [!NOTE]  
>  La propriété **CommandTimeout** de la source Excel n’est pas disponible dans **l’Éditeur de source Excel**, mais peut être définie à l’aide de **l’Éditeur avancé**. Pour plus d’informations sur cette propriété, consultez la section sur la source Excel dans [Propriétés personnalisées d’Excel](../../integration-services/data-flow/excel-custom-properties.md).  
  
 Pour en savoir plus sur la source Excel, consultez [Excel Source](../../integration-services/data-flow/excel-source.md).  
  
## Options statiques  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions Excel existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Gestionnaire de connexions Excel**.  
  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Table ou vue|Récupérez des données à partir d'une feuille de calcul ou d'une plage nommée dans le fichier Excel.|  
|Variable de nom de table ou de vue|Spécifiez le nom de la feuille de calcul ou de la plage dans une variable.<br /><br /> **Informations connexes :** [Utiliser des variables dans des packages](../Topic/Use%20Variables%20in%20Packages.md)|  
|Commande SQL|Récupérez des données à partir du fichier Excel à l'aide d'une requête SQL. Pour plus d’informations sur la syntaxe de la requête, consultez [Source Excel](../../integration-services/data-flow/excel-source.md).|  
|Commande SQL à partir d'une variable|Spécifiez le texte de la requête SQL dans une variable.|  
  
 **Aperçu**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Vue de données**. L'aperçu peut afficher jusqu'à 200 lignes.  
  
## Options dynamiques du mode d'accès aux données  
  
### Mode d'accès aux données = Table ou vue  
 **Nom de la feuille Excel**  
 Sélectionnez le nom de la feuille de calcul ou de la plage nommée dans la liste des éléments disponibles dans le classeur Excel.  
  
### Mode d'accès aux données = Variable de nom de table ou de vue  
 **Nom de la variable**  
 Sélectionnez la variable contenant le nom de la feuille de calcul ou de la plage nommée.  
  
### Mode d'accès aux données = Commande SQL  
 **Texte de la commande SQL**  
 Entrez le texte d’une requête SQL, créez la requête en cliquant sur **Générer une requête** ou parcourez l’arborescence jusqu’au fichier qui contient le texte de la requête en cliquant sur **Parcourir**.  
  
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
 [Éditeur de source Excel &#40;page Colonnes&#41;](../../integration-services/data-flow/excel-source-editor-columns-page.md)   
 [Éditeur de source Excel &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/excel-source-editor-error-output-page.md)   
 [Gestionnaire de connexions Excel](../../integration-services/connection-manager/excel-connection-manager.md)   
 [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  