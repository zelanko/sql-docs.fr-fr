---
title: Créer la Structure d’exploration de données (SQL Server Data Mining Add-ins) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: b8b1eedc-4d6d-4429-a578-e629ec573934
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 166689f175485af66ca140f82fa968512baf8519
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086339"
---
# <a name="create-mining-structure-sql-server-data-mining-add-ins"></a>Créer une structure d'exploration de données (Compléments d'exploration de données SQL Server)
  ![Bouton de créer une Structure d’exploration de données, ruban Exploration de données](media/dmc-createstruct.gif "bouton Créer la Structure d’exploration de données, ruban Exploration de données")  
  
 Utilisez le **avancé** option dans le **modélisation des données** lorsque vous souhaitez créer un jeu de données utilisé pour l’analyse sans nécessairement créer un modèle de groupe. Cela est utile lorsque vous souhaitez tester différents algorithmes.  
  
 Après avoir créé la structure d’exploration de données, utilisez le [ajouter le modèle à la Structure](add-model-to-structure-data-mining-add-ins-for-excel.md) Assistant pour créer un modèle basé sur cette structure. Vous pouvez également créer de nouveaux modèles à l’aide de la **éditeur de requêtes d’avancé d’exploration de données**.  
  
 Utilisez également cette option si vous envisagez de générer des modèles à l'aide de l'un des algorithmes avancés, pris en charge par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] mais non disponibles dans les Assistants, tels que le modèle de régression linéaire ou Sequence Clustering, ou si vous utilisez un algorithme personnalisé.  
  
> [!NOTE]  
>  Lorsque vous créez la structure d'exploration de données, vous pouvez également créer un jeu de données de test sélectionné de façon aléatoire que pouvez utiliser pour valider tous vos modèles. Cela est pratique, car vous pouvez facilement comparer la précision du modèle par rapport à un jeu de données commun. Sélectionnez simplement l’option, **fractionner les données d’apprentissage et jeux de test** et spécifiez un pourcentage approprié de données à réserver pour les tests, généralement environ 30 pour cent.  
  
## <a name="use-the-wizard-to-create-a-mining-structure"></a>Utiliser l'Assistant pour créer une structure d'exploration de données  
  
1.  Dans le **d’exploration de données** ruban, cliquez sur **avancé**, puis sélectionnez **Create Structure**.  
  
2.  Dans le **sélectionner les données source** boîte de dialogue, spécifiez la plage Excel, une table de données Excel ou une source de données externe qui contient les données que vous souhaitez utiliser pour l’analyse.  
  
     Cliquez sur **Suivant**.  
  
3.  Dans le **sélectionner des colonnes** boîte de dialogue zone, passez en revue la liste des colonnes disponibles dans la source de données sélectionnée.  
  
4.  Cliquez sur la flèche à droite du nom de colonne pour modifier le **utilisation** de la colonne, en choisissant des valeurs suivantes :  
  
    -   **Key**. Chaque modèle requiert au moins une clé.  
  
    -   **Temps clé**. Cette option est disponible uniquement pour les modèles de prévision, si nécessaire.  
  
    -   **Inclure**. Indique que la colonne doit être disponible dans la structure d'exploration de données, mais n'est pas une colonne clé.  
  
    -   **N’utilisez pas**. Indique que la colonne ne doit pas être incluse dans la structure d'exploration de données.  
  
     N'oubliez pas que vous pouvez toujours ignorer des colonnes lorsque vous créez le modèle, mais pour ajouter des colonnes ultérieurement, vous devez retraiter la structure et le modèle.  
  
5.  Cliquez sur le bouton de navigation **(...)**  bouton pour définir le type de contenu, type de données et des indicateurs de modélisation.  
  
    > [!NOTE]  
    >  Si la colonne contient des données numériques, vous devez toujours ouvrir cette boîte de dialogue pour vérifier que type de données approprié est sélectionné. Dans certains cas, même si les données d'entrée sont des nombres, vous pouvez les traiter en tant que variable catégorielle, ou valeur discrète, plutôt que nombre continu.  
    >   
    >  Par exemple, une colonne de code postal peut être répertoriée par défaut comme un type de données Long continu, mais pour obtenir de meilleurs résultats, vous pouvez spécifier qu'elle doit être gérée comme une valeur texte discrète.  
    >   
    >  Pour plus d’informations, consultez la section sur les types de contenu dans [en choisissant des données pour l’exploration de données](choosing-data-for-data-mining.md).  
  
     Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
6.  Cliquez sur **Suivant**.  
  
     Selon le type de données que vous utilisez, vous pouvez exécuter l'Assistant après cette étape. Dans ce cas, passez directement à la **Terminer** page pour nommer votre structure d’exploration de données.  
  
     Pour les autres modèles, vous disposez d'une option supplémentaire permettant de créer un jeu de données de test.  
  
7.  Dans le **fractionner les données d’apprentissage et jeux de données de test** boîte de dialogue, spécifiez comment vous souhaitez que vos données soient partitionnées. Par défaut, 30 pour cent de données sont utilisés pour le test.  
  
     Le cas échéant, tapez le nombre maximum de lignes à utiliser pour le test.  
  
     Cliquez sur **Suivant**.  
  
8.  Dans le **Terminer** boîte de dialogue, tapez un nom et une description pour la nouvelle structure d’exploration de données.  
  
9. Cliquez sur **Terminer**.  
  
### <a name="related-options"></a>Options connexes  
  
|Option|Commentaires|  
|------------|--------------|  
|**Sélectionnez la Source de données** boîte de dialogue|Lorsque vous sélectionnez une table Excel, vous devez indiquer si les données ont déjà des en-têtes. Si vous ignorez cette opération, la première ligne de données est utilisée comme nom de colonne.<br /><br /> Si vous utilisez l’option, **source de données externe**, vous pouvez utiliser n’importe quel type de données qui peuvent être définies dans un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] source de données. Toutefois, la boîte de dialogue du complément pour créer de nouvelles sources de données n'inclut pas la plage complète des sources de données prises en charge par Analysis Services. Nous vous recommandons de créer les sources de données sur le serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] à l'avance, puis de vous connecter à l'aide des compléments.|  
|**Éditeur de requête de Source de données** boîte de dialogue|Après vous être connecté à la source de données spécifiée, ajoutez des colonnes ou créez une requête personnalisée pour générer des colonnes personnalisées.|  
|**Fractionner les données d’apprentissage et jeux de données de test**|La valeur recommandée pour l’apprentissage et jeux de test est de 70 pour cent pour l’apprentissage et 30 pour cent pour les tests ; Toutefois, si vous avez une grande quantité de données, vous pouvez spécifier un nombre maximal de lignes pour le test.|  
|Boîte de dialogue Terminer|Les options d'extraction sont disponibles sur certains types de modèle et sont très utiles si vous avez inclus les colonnes de détail dans la structure d'exploration de données. Par exemple, si vous créez un modèle de clustering, vous pouvez inclure des informations telles que le nom ou l'adresse de messagerie pour l'extraction mais pas pour l'analyse, afin de simplifier le contact avec les clients dans un cluster particulier.|  
  
###  <a name="Bkmk_strctcolumn"></a> Définition de l’utilisation des colonnes dans l’Assistant de Structure d’exploration de données  
 Lorsque vous créez une nouvelle structure d'exploration de données, vous pouvez spécifier les colonnes de la source de données à y inclure, ainsi que le mode d'utilisation de ces colonnes. N'oubliez pas qu'une structure d'exploration de données peut prendre en charge plusieurs modèles d'exploration de données.  
  
|Valeurs|Description|  
|------------|-----------------|  
|**inclure**|Spécifie que la colonne contient des données qui peuvent être utilisées pour l'analyse ou la prédiction.|  
|**Clé**|Spécifie que la colonne contient un ID de transaction, un ID de série ou une autre clé nécessaire au traitement.<br /><br /> Tous les algorithmes nécessitent une colonne Clé. Certains algorithmes n'autorisent toutefois qu'une seule clé, tandis que d'autres en autorisent plusieurs.<br /><br /> Si la colonne contient une clé mais n’est pas obligatoire pour le traitement, sélectionnez **n’utilisent pas**.|  
|**Temps clé**|Spécifie que la colonne contient une date ou une autre valeur numérique qui peut être utilisée pour identifier de façon unique les éléments d'une série chronologique.|  
|**N’utilisez pas**|Spécifie que la colonne doit être ignorée. Les données de la colonne ne seront pas traitées.|  
  
 Pour traiter correctement un modèle, l'algorithme doit savoir quelle est la colonne clé qui identifie de manière unique chaque ligne, quelle est la colonne cible pour la création des prédictions si vous créez un modèle prévisible et quelles colonnes utiliser comme colonnes d'entrée pour créer les relations qui prévoient la colonne cible.  
  
-   Colonnes qui sont spécifiées en tant que **n’utilisez pas** ne seront plus disponibles dans la structure d’exploration de données.  
  
     Si vous ajoutez des colonnes inutiles ou que des valeurs sont erronées, les résultats de l'analyse peuvent en être affectés. Vous devez donc veiller à n'inclure que les colonnes pertinentes. N'oubliez toutefois pas que les colonnes que vous n'utilisez pas dans la structure d'exploration de données ne seront pas disponibles pour l'interrogation.  
  
-   Colonnes qui sont spécifiées en tant que le **Include** type seront inclus dans la structure d’exploration de données et peuvent être utilisé ultérieurement pour l’analyse ou la prédiction dans les modèles d’exploration de données.  
  
     Si vous n'êtes pas certain d'avoir à utiliser une colonne, vous pouvez toujours l'inclure dans la structure d'exploration de données, puis créer un modèle d'exploration de données qui ne l'utilise pas. Vous pouvez par exemple inclure une colonne de numéro de téléphone dans vos données pour référence ultérieure, mais créer un modèle de clustering qui ignore les numéros de téléphone. Une fois les clusters créés, vous pouvez créer une requête qui retourne les numéros de téléphone des personnes appartenant à un cluster donné.  
  
-   Tous les algorithmes nécessitent un **clé** colonne. Les valeurs de la colonne Clé doivent être uniques. Un **Key Time** colonne est uniquement requis pour la prévision ou de série chronologique modèles. .  
  
### <a name="requirements"></a>Spécifications  
 Pour créer une structure d'exploration de données, vous devez disposer d'une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La connexion est requise même si vous utilisez des structures temporaires. Pour plus d’informations sur la création ou modification d’une connexion, consultez [se connecter à la Source de données &#40;Client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)  
  
  
