---
title: Éditeur de source Excel (page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsourceadapter.connection.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c3132bd65bb6f3092cc950758d4f346b5c4cd8fd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66059167"
---
# <a name="excel-source-editor-connection-manager-page"></a>Éditeur de source Excel (page Gestionnaire de connexions)
  Le nœud **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de source Excel** vous permet de sélectionner le classeur [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] de la source à utiliser. La source Excel lit les données à partir d'une feuille de calcul ou d'une plage nommée dans un classeur existant.  
  
> [!NOTE]  
>  La `CommandTimeout` propriété de la source Excel n’est pas disponible dans l **'éditeur de source Excel**, mais elle peut être définie à l’aide de l' **éditeur avancé**. Pour plus d’informations sur cette propriété, consultez la section sur la source Excel dans [Propriétés personnalisées d’Excel](data-flow/excel-custom-properties.md).  
  
 Pour en savoir plus sur la source Excel, consultez [Excel Source](data-flow/excel-source.md).  
  
## <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions Excel existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Gestionnaire de connexions Excel** .  
  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Table ou vue|Récupérez des données à partir d'une feuille de calcul ou d'une plage nommée dans le fichier Excel.|  
|Variable de nom de table ou de vue|Spécifiez le nom de la feuille de calcul ou de la plage dans une variable.<br /><br /> **Informations connexes :** [utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md)|  
|Commande SQL|Récupérez des données à partir du fichier Excel à l'aide d'une requête SQL. Pour plus d’informations sur la syntaxe de la requête, consultez [Source Excel](data-flow/excel-source.md).|  
|Commande SQL à partir d'une variable|Spécifiez le texte de la requête SQL dans une variable.|  
  
 **Préversion**  
 Affichez un aperçu des résultats à partir de la boîte de dialogue **Vue de données** . L'aperçu peut afficher jusqu'à 200 lignes.  
  
## <a name="data-access-mode-dynamic-options"></a>Options dynamiques du mode d'accès aux données  
  
### <a name="data-access-mode--table-or-view"></a>Mode d'accès aux données = Table ou vue  
 **Nom de la feuille Excel**  
 Sélectionnez le nom de la feuille de calcul ou de la plage nommée dans la liste des éléments disponibles dans le classeur Excel.  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Mode d'accès aux données = Variable de nom de table ou de vue  
 **Nom de la variable**  
 Sélectionnez la variable contenant le nom de la feuille de calcul ou de la plage nommée.  
  
### <a name="data-access-mode--sql-command"></a>Mode d'accès aux données = Commande SQL  
 **Texte de la commande SQL**  
 Entrez le texte d’une requête SQL, créez la requête en cliquant sur **Générer une requête**ou parcourez l’arborescence jusqu’au fichier qui contient le texte de la requête en cliquant sur **Parcourir**.  
  
 **Paramètres**  
 Si vous avez entré une requête paramétrable en spécifiant ? comme espace réservé de paramètre dans le texte de la requête, utilisez la boîte de dialogue **Définition des paramètres de la requête** pour mapper des paramètres d’entrée de la requête à des variables du package.  
  
 **Générer la requête**  
 Utilisez la boîte de dialogue **Générateur de requêtes** pour construire la requête SQL visuellement.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir** , localisez le fichier qui contient le texte de la requête SQL.  
  
 **Analyser la requête**  
 Vérifiez la syntaxe du texte de la requête.  
  
### <a name="data-access-mode--sql-command-from-variable"></a>Mode d'accès aux données = Commande SQL à partir d'une variable  
 **Nom de la variable**  
 Sélectionnez la variable qui contient le texte de la requête SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de source Excel &#40;page colonnes&#41;](../../2014/integration-services/excel-source-editor-columns-page.md)   
 [Éditeur de source Excel &#40;page sortie d’erreur&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md)   
 [Gestionnaire de connexions Excel](connection-manager/excel-connection-manager.md)   
 [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](control-flow/foreach-loop-container.md)  
  
  
