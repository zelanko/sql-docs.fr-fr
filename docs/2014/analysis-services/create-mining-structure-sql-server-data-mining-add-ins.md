---
title: Créer une structure d’exploration de données (compléments d’exploration de données SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: b8b1eedc-4d6d-4429-a578-e629ec573934
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ae5244110e6b95434f9008fd7dc99cee259acf8c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66086816"
---
# <a name="create-mining-structure-sql-server-data-mining-add-ins"></a>Créer une structure d'exploration de données (Compléments d'exploration de données SQL Server)
  ![Bouton Créer une structure d'exploration de données, ruban Exploration de données](media/dmc-createstruct.gif "Bouton Créer une structure d'exploration de données, ruban Exploration de données")  
  
 Utilisez l’option **avancé** dans le groupe **modélisation des données** lorsque vous souhaitez créer un jeu de données utilisé pour l’analyse sans nécessairement créer un modèle. Cela est utile lorsque vous souhaitez tester différents algorithmes.  
  
 Une fois que vous avez créé la structure d’exploration de données, utilisez l’Assistant [Ajout d’un modèle à une structure](add-model-to-structure-data-mining-add-ins-for-excel.md) pour créer un modèle basé sur cette structure. Vous pouvez également créer des modèles à l’aide de l' **éditeur de requêtes avancé d’exploration de données**.  
  
 Utilisez également cette option si vous envisagez de générer des modèles à l'aide de l'un des algorithmes avancés, pris en charge par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] mais non disponibles dans les Assistants, tels que le modèle de régression linéaire ou Sequence Clustering, ou si vous utilisez un algorithme personnalisé.  
  
> [!NOTE]  
>  Lorsque vous créez la structure d'exploration de données, vous pouvez également créer un jeu de données de test sélectionné de façon aléatoire que pouvez utiliser pour valider tous vos modèles. Cela est pratique, car vous pouvez facilement comparer la précision du modèle par rapport à un jeu de données commun. Il vous suffit de sélectionner l’option, de **fractionner les données en jeux d’apprentissage et de test** et de spécifier un pourcentage approprié de données à réserver pour les tests, généralement environ 30%.  
  
## <a name="use-the-wizard-to-create-a-mining-structure"></a>Utiliser l'Assistant pour créer une structure d'exploration de données  
  
1.  Dans le ruban **exploration de données** , cliquez sur **avancé**, puis sélectionnez créer une **structure**.  
  
2.  Dans la boîte de dialogue **Sélectionner les données source** , spécifiez la plage Excel, la table de données Excel ou la source de données externe qui contient les données que vous souhaitez utiliser pour l’analyse.  
  
     Cliquez sur **Suivant**.  
  
3.  Dans la boîte de dialogue **Sélectionner les colonnes** , passez en revue la liste des colonnes disponibles dans la source de données sélectionnée.  
  
4.  Cliquez sur la flèche à droite du nom de la colonne pour modifier l' **utilisation** de la colonne, en choisissant l’une des valeurs suivantes :  
  
    -   **Clé**. Chaque modèle requiert au moins une clé.  
  
    -   **Temps clé**. Cette option est disponible uniquement pour les modèles de prévision, si nécessaire.  
  
    -   **Incluez**. Indique que la colonne doit être disponible dans la structure d'exploration de données, mais n'est pas une colonne clé.  
  
    -   **N’utilisez pas**. Indique que la colonne ne doit pas être incluse dans la structure d'exploration de données.  
  
     N'oubliez pas que vous pouvez toujours ignorer des colonnes lorsque vous créez le modèle, mais pour ajouter des colonnes ultérieurement, vous devez retraiter la structure et le modèle.  
  
5.  Cliquez sur le bouton Parcourir **(...)** pour définir le type de contenu, le type de données et les indicateurs de modélisation.  
  
    > [!NOTE]  
    >  Si la colonne contient des données numériques, vous devez toujours ouvrir cette boîte de dialogue pour vérifier que type de données approprié est sélectionné. Dans certains cas, même si les données d'entrée sont des nombres, vous pouvez les traiter en tant que variable catégorielle, ou valeur discrète, plutôt que nombre continu.  
    >   
    >  Par exemple, une colonne de code postal peut être répertoriée par défaut comme un type de données Long continu, mais pour obtenir de meilleurs résultats, vous pouvez spécifier qu'elle doit être gérée comme une valeur texte discrète.  
    >   
    >  Pour plus d’informations, consultez la section sur les types de contenu dans [choix des données pour l’exploration de données](choosing-data-for-data-mining.md).  
  
     Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
6.  Cliquez sur **Suivant**.  
  
     Selon le type de données que vous utilisez, vous pouvez exécuter l'Assistant après cette étape. Dans ce cas, passez directement à la page **Terminer** pour nommer votre structure d’exploration de données.  
  
     Pour les autres modèles, vous disposez d'une option supplémentaire permettant de créer un jeu de données de test.  
  
7.  Dans la boîte de dialogue **fractionner les données en jeux de données d’apprentissage et de test** , spécifiez la façon dont vous souhaitez partitionner vos données. Par défaut, 30 pour cent de données sont utilisés pour le test.  
  
     Le cas échéant, tapez le nombre maximum de lignes à utiliser pour le test.  
  
     Cliquez sur **Suivant**.  
  
8.  Dans la boîte de dialogue **Terminer** , tapez un nom et une description pour la nouvelle structure d’exploration de données.  
  
9. Cliquez sur **Terminer**.  
  
### <a name="related-options"></a>Options connexes  
  
|Option|Commentaires|  
|------------|--------------|  
|Boîte de dialogue **Sélectionner les données source**|Lorsque vous sélectionnez une table Excel, vous devez indiquer si les données ont déjà des en-têtes. Si vous ignorez cette opération, la première ligne de données est utilisée comme nom de colonne.<br /><br /> Si vous utilisez l’option **source de données externe**, vous pouvez utiliser n’importe quel type de données pouvant être défini dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] une source de données. Toutefois, la boîte de dialogue du complément pour créer de nouvelles sources de données n'inclut pas la plage complète des sources de données prises en charge par Analysis Services. Nous vous recommandons de créer les sources de données sur le serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à l'avance, puis de vous connecter à l'aide des compléments.|  
|**Éditeur de requête de source de données** , boîte de dialogue|Après vous être connecté à la source de données spécifiée, ajoutez des colonnes ou créez une requête personnalisée pour générer des colonnes personnalisées.|  
|**Fractionner les données en jeux d'apprentissage et jeux de test**|La valeur recommandée pour l’apprentissage et les jeux de test est de 70% pour la formation et de 30% pour les tests. Toutefois, si vous avez beaucoup de données, vous pouvez spécifier un nombre maximal de lignes à tester.|  
|Boîte de dialogue Terminer|Les options d'extraction sont disponibles sur certains types de modèle et sont très utiles si vous avez inclus les colonnes de détail dans la structure d'exploration de données. Par exemple, si vous créez un modèle de clustering, vous pouvez inclure des informations telles que le nom ou l'adresse de messagerie pour l'extraction mais pas pour l'analyse, afin de simplifier le contact avec les clients dans un cluster particulier.|  
  
###  <a name="setting-column-usage-in-the-create-mining-structure-wizard"></a><a name="Bkmk_strctcolumn"></a>Définition de l’utilisation des colonnes dans l’Assistant Création d’une structure d’exploration de données  
 Lorsque vous créez une nouvelle structure d'exploration de données, vous pouvez spécifier les colonnes de la source de données à y inclure, ainsi que le mode d'utilisation de ces colonnes. N'oubliez pas qu'une structure d'exploration de données peut prendre en charge plusieurs modèles d'exploration de données.  
  
|Valeurs|Description|  
|------------|-----------------|  
|**Inclure**|Spécifie que la colonne contient des données qui peuvent être utilisées pour l'analyse ou la prédiction.|  
|**Clé**|Spécifie que la colonne contient un ID de transaction, un ID de série ou une autre clé nécessaire au traitement.<br /><br /> Tous les algorithmes nécessitent une colonne Clé. Certains algorithmes n'autorisent toutefois qu'une seule clé, tandis que d'autres en autorisent plusieurs.<br /><br /> Si la colonne contient une clé mais n’est pas requise pour le traitement, sélectionnez **ne pas utiliser**.|  
|**Temps clé**|Spécifie que la colonne contient une date ou une autre valeur numérique qui peut être utilisée pour identifier de façon unique les éléments d'une série chronologique.|  
|**Ne pas utiliser**|Spécifie que la colonne doit être ignorée. Les données de la colonne ne seront pas traitées.|  
  
 Pour traiter correctement un modèle, l'algorithme doit savoir quelle est la colonne clé qui identifie de manière unique chaque ligne, quelle est la colonne cible pour la création des prédictions si vous créez un modèle prévisible et quelles colonnes utiliser comme colonnes d'entrée pour créer les relations qui prévoient la colonne cible.  
  
-   Les colonnes spécifiées comme **n’utilisent pas** ne sont pas présentes dans la structure d’exploration de données.  
  
     Si vous ajoutez des colonnes inutiles ou que des valeurs sont erronées, les résultats de l'analyse peuvent en être affectés. Vous devez donc veiller à n'inclure que les colonnes pertinentes. N'oubliez toutefois pas que les colonnes que vous n'utilisez pas dans la structure d'exploration de données ne seront pas disponibles pour l'interrogation.  
  
-   Les colonnes spécifiées en tant que type **include** sont incluses dans la structure d’exploration de données et peuvent être utilisées ultérieurement pour l’analyse ou la prédiction dans les modèles d’exploration de données.  
  
     Si vous n'êtes pas certain d'avoir à utiliser une colonne, vous pouvez toujours l'inclure dans la structure d'exploration de données, puis créer un modèle d'exploration de données qui ne l'utilise pas. Vous pouvez par exemple inclure une colonne de numéro de téléphone dans vos données pour référence ultérieure, mais créer un modèle de clustering qui ignore les numéros de téléphone. Une fois les clusters créés, vous pouvez créer une requête qui retourne les numéros de téléphone des personnes appartenant à un cluster donné.  
  
-   Tous les algorithmes nécessitent une colonne **clé** . Les valeurs de la colonne Clé doivent être uniques. Une colonne **Key Time** n’est requise que pour les modèles de prévision ou de série chronologique. .  
  
### <a name="requirements"></a>Conditions requises  
 Pour créer une structure d'exploration de données, vous devez disposer d'une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La connexion est requise même si vous utilisez des structures temporaires. Pour plus d’informations sur la création ou la modification d’une connexion, consultez [se connecter à des données sources &#40;client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d'un modèle d'exploration de données](creating-a-data-mining-model.md)  
  
  
