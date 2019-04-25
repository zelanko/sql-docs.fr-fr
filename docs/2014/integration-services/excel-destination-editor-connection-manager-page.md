---
title: Éditeur de Destination Excel (Page Gestionnaire de connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldestadapter.connection.f1
helpviewer_keywords:
- Excel Destination Editor
ms.assetid: fc13f725-963c-488e-91e2-20627133e842
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f790e0cc9193f2f31c7f021c4d4901e7a825fb13
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62769735"
---
# <a name="excel-destination-editor-connection-manager-page"></a>Éditeur de destination Excel (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination Excel** pour spécifier des informations sur la source de données et afficher un aperçu des résultats. La destination Excel charge les données dans une feuille de calcul ou dans une plage (de cellules) nommée d'un classeur [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] .  
  
> [!NOTE]  
>  Le `CommandTimeout` propriété de la destination Excel n’est pas disponible dans le **éditeur de Destination Excel**, mais peut être définie à l’aide de la **éditeur avancé**. De plus, certaines options de chargement rapide sont uniquement disponibles dans l' **Éditeur avancé**. Pour plus d'informations sur ces propriétés, consultez la section sur la destination Excel dans [Excel Custom Properties](data-flow/excel-custom-properties.md).  
  
 Pour en savoir plus sur la destination Excel, consultez [Excel Destination](data-flow/excel-destination.md).  
  
## <a name="static-options"></a>Options statiques  
 **Gestionnaire de connexions Excel**  
 Sélectionnez un gestionnaire de connexions Excel existant dans la liste ou créez une connexion en cliquant sur **Nouveau**.  
  
 **Nouveau**  
 Créez un gestionnaire de connexions à l’aide de la boîte de dialogue **Gestionnaire de connexions Excel** .  
  
 **Mode d'accès aux données**  
 Spécifiez la méthode de sélection des données dans la source.  
  
|Option|Description|  
|------------|-----------------|  
|Table ou vue|Charge les données dans une feuille de calcul ou dans une plage nommée de la source de données Excel.|  
|Variable de nom de table ou de vue|Spécifiez le nom de la feuille de calcul ou de la plage dans une variable.<br /><br /> **Informations connexes** : [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md)|  
|Commande SQL|Charge les données dans la destination Excel à l'aide d'une requête SQL.|  
  
 **Nom de la feuille Excel**  
 Sélectionnez la destination Excel dans la liste déroulante. Si la liste est vide, cliquez sur **Nouveau**.  
  
 **Nouveau**  
 Cliquez sur **Nouveau** pour ouvrir la boîte de dialogue **Créer une table** . Lorsque vous cliquez sur **OK**, la boîte de dialogue crée le fichier Excel vers lequel le **Gestionnaire de connexions Excel** pointe.  
  
 **Afficher les données existantes**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Visualiser les résultats de la requête** . L'aperçu peut afficher jusqu'à 200 lignes.  
  
> [!WARNING]  
>  Si le **Gestionnaire de connexions Excel** que vous avez sélectionné pointe vers un fichier Excel qui n’existe pas, vous voyez un message d’erreur quand vous cliquez sur ce bouton.  
  
## <a name="data-access-mode-dynamic-options"></a>Options dynamiques du mode d'accès aux données  
  
### <a name="data-access-mode--table-or-view"></a>Mode d'accès aux données = Table ou vue  
 **Nom de la feuille Excel**  
 Sélectionnez le nom de la feuille de calcul ou de la plage nommée dans une liste des feuilles ou plages disponibles dans la source de données.  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a>Mode d'accès aux données = Variable de nom de table ou de vue  
 **Nom de la variable**  
 Sélectionnez la variable contenant le nom de la feuille de calcul ou de la plage nommée.  
  
### <a name="data-access-mode--sql-command"></a>Mode d'accès aux données = Commande SQL  
 **Texte de la commande SQL**  
 Entrez le texte de la requête SQL, générez la requête en cliquant sur **Générer la requête**ou cliquez sur **Parcourir**pour accéder au fichier contenant le texte de la requête.  
  
 **Générer la requête**  
 Utilisez la boîte de dialogue **Générateur de requêtes** pour construire la requête SQL visuellement.  
  
 **Parcourir**  
 Dans la boîte de dialogue **Ouvrir** , localisez le fichier qui contient le texte de la requête SQL.  
  
 **Analyser la requête**  
 Vérifiez la syntaxe du texte de la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination Excel &#40;page Mappages&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md)   
 [Éditeur de destination Excel &#40;page Sortie d’erreur&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md)   
 [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](control-flow/foreach-loop-container.md)  
  
  
