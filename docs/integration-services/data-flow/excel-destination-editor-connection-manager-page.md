---
title: "&#201;diteur de destination Excel (page Gestionnaire de connexions) | Microsoft Docs"
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
  - "sql13.dts.designer.exceldestadapter.connection.f1"
helpviewer_keywords: 
  - "Éditeur de destination Excel"
ms.assetid: fc13f725-963c-488e-91e2-20627133e842
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# &#201;diteur de destination Excel (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination Excel** pour spécifier des informations sur la source de données et afficher un aperçu des résultats. La destination Excel charge les données dans une feuille de calcul ou dans une plage (de cellules) nommée d'un classeur [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] .  
  
> [!NOTE]  
>  La propriété **CommandTimeout** de la destination Excel n'est pas disponible dans l' **Éditeur de destination Excel**, mais peut être définie à l'aide de l' **Éditeur avancé**. De plus, certaines options de chargement rapide sont uniquement disponibles dans l' **Éditeur avancé**. Pour plus d'informations sur ces propriétés, consultez la section sur la destination Excel dans [Excel Custom Properties](../../integration-services/data-flow/excel-custom-properties.md).  
  
 Pour en savoir plus sur la destination Excel, consultez [Excel Destination](../../integration-services/data-flow/excel-destination.md).  
  
## Options statiques  
 **Gestionnaire de connexions Excel**  
 Sélectionnez un gestionnaire de connexions Excel existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Gestionnaire de connexions Excel**.  
  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Option|Description|  
|------------|-----------------|  
|Table ou vue|Charge les données dans une feuille de calcul ou dans une plage nommée de la source de données Excel.|  
|Variable de nom de table ou de vue|Spécifiez le nom de la feuille de calcul ou de la plage dans une variable.<br /><br /> **Informations connexes** : [Utiliser des variables dans des packages](../Topic/Use%20Variables%20in%20Packages.md)|  
|Commande SQL|Charge les données dans la destination Excel à l'aide d'une requête SQL.|  
  
 **Nom de la feuille Excel**  
 Sélectionnez la destination Excel dans la liste déroulante. Si la liste est vide, cliquez sur **Nouveau**.  
  
 **Nouveau**  
 Cliquez sur **Nouveau** pour ouvrir la boîte de dialogue **Créer une table**. Lorsque vous cliquez sur **OK**, la boîte de dialogue crée le fichier Excel vers lequel le **Gestionnaire de connexions Excel** pointe.  
  
 **Afficher les données existantes**  
 Affiche un aperçu des résultats à l’aide de la boîte de dialogue **Visualiser les résultats de la requête**. L'aperçu peut afficher jusqu'à 200 lignes.  
  
> [!WARNING]  
>  Si le **Gestionnaire de connexions Excel** que vous avez sélectionné pointe vers un fichier Excel qui n’existe pas, vous voyez un message d’erreur quand vous cliquez sur ce bouton.  
  
## Options dynamiques du mode d'accès aux données  
  
### Mode d'accès aux données = Table ou vue  
 **Nom de la feuille Excel**  
 Sélectionnez le nom de la feuille de calcul ou de la plage nommée dans une liste des feuilles ou plages disponibles dans la source de données.  
  
### Mode d'accès aux données = Variable de nom de table ou de vue  
 **Nom de la variable**  
 Sélectionnez la variable contenant le nom de la feuille de calcul ou de la plage nommée.  
  
### Mode d'accès aux données = Commande SQL  
 **Texte de la commande SQL**  
 Entrez le texte de la requête SQL, générez la requête en cliquant sur **Générer la requête** ou cliquez sur **Parcourir** pour accéder au fichier contenant le texte de la requête.  
  
 **Construire la requête**  
 Utilisez la boîte de dialogue **Générateur de requêtes** pour construire la requête SQL visuellement.  
  
 **Parcourir**  
 Utilisez la boîte de dialogue **Ouvrir** pour accéder au fichier contenant le texte de la requête SQL.  
  
 **Analyser la requête**  
 Vérifiez la syntaxe du texte de la requête.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination Excel &#40;page Mappages&#41;](../../integration-services/data-flow/excel-destination-editor-mappings-page.md)   
 [Éditeur de destination Excel &#40;page Sortie d’erreur&#41;](../../integration-services/data-flow/excel-destination-editor-error-output-page.md)   
 [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  