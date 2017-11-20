---
title: "Se connecter à une Source de données de fichier plat (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7e7067b-f5a5-482f-b97e-9d82fe8e9f76
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: 568d02ef58102b47501415d35f64369e997e875b
ms.contentlocale: fr-fr
ms.lasthandoff: 10/18/2017

---
# <a name="connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard"></a>Se connecter à une Source de données de fichier plat (SQL Server Assistant Importation et exportation)
Cette rubrique vous montre comment se connecter à un **fichier plat** de source de données (fichier texte) à partir de la **choisir une Source de données** ou **choisir une Destination** page de l’importation de SQL Server et l’Assistant Exportation. Pour les fichiers plats, ces deux pages de l’Assistant présentent différents jeux d’options, afin de cette rubrique décrit la source de fichier plat et la destination de fichier plat séparément.

## <a name="an-alternative-for-simple-text-import"></a>Une autre solution pour l’importation de texte simple
Si vous devez importer un fichier texte dans SQL Server, et vous ne devez pas toutes les options de configuration disponibles dans l’Assistant Importation et exportation, envisagez d’utiliser le **Assistant Importation de fichier plat** dans SQL Server Management Studio (SSMS). Pour plus d’informations, consultez les articles suivants :
- [Nouveautés de SQL Server Management Studio 17.3 ](https://blogs.technet.microsoft.com/dataplatforminsider/2017/10/10/whats-new-in-sql-server-management-studio-17-3/)
- [Présentation du nouvel Assistant Importation de fichier plat dans SSMS 17.3](https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-new-Import-Flat-File-Wizard-in-SSMS-173)

## <a name="connect-to-a-flat-file-source"></a>Se connecter à une source de fichier plat
 
 Il existe quatre pages d’options pour les sources de données de fichier plat. C’est un grand nombre de pages ! Mais vous n’êtes pas obligé de perdre du temps sur chaque page. Voici les tâches à prendre en compte.
 
Radiomessagerie|Recommandation  |Type  
----|---------|---------
**Général**|Assurez-vous que vous mettez à jour les options de la **Format** section.|Recommandation    
**Columns**|Assurez-vous que vous archivez les séparateurs de colonne et de ligne (pour un fichier délimité) ou que vous sélectionnez les colonnes (pour un fichier de largeur fixe).|Recommandation
**Avancé**|Si vous le souhaitez, vérifiez les types de données et d’autres propriétés attribuées par défaut pour les colonnes.|Ce paramètre est facultatif
**Aperçu**|Si vous le souhaitez, prévisualiser un échantillon de données, en utilisant les paramètres que vous avez spécifié.|Ce paramètre est facultatif

## <a name="general-page-source"></a>Page Général (source)
 Dans la page **Général**, accédez au fichier, puis vérifiez les paramètres de la section **Format**.
 
 ![Page Général de la connexion à un fichier plat](../../integration-services/import-export-data/media/flat-file-connection-general.png)  

### <a name="options-to-specify-general-page"></a>Options pour spécifier (**général** page)

 **Nom de fichier**  
 Entrez le chemin d’accès et le nom du fichier plat.  
  
 **Parcourir**  
 Recherchez le fichier plat.  
  
 **Paramètres régionaux**  
 Spécifiez les paramètres régionaux pour fournir des informations spécifiques au langage pour le tri et pour les formats de date et d’heure.  
  
 **Unicode**  
 Spécifiez si le fichier utilise Unicode. Si vous utilisez Unicode, vous ne pouvez pas spécifier une page de codes.  
  
 **Page de codes**  
 Spécifiez la page de codes pour du texte non-Unicode.  
  
 **Format**  
 Déterminez si le fichier utilise délimité, largeur fixe ou en drapeau à la mise en forme à droite.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Délimité|Les colonnes sont séparées par des délimiteurs. Vous spécifiez le délimiteur sur le **colonnes** page.|  
|Largeur fixe|Les colonnes ont une largeur fixe.|  
|En drapeau à droite|Dans les fichiers en drapeau à droite, chaque colonne a une largeur fixe, sauf la dernière qui est délimitée par le séparateur de lignes.|  
  
 **Qualificateur de texte**  
 Spécifiez le qualificateur de texte, utilisée par le fichier. Par exemple, vous pouvez spécifier que les champs de texte soient placés entre guillemets. (Cette propriété s’applique uniquement aux fichiers de délimité.) 
  
> [!NOTE]
> Après avoir sélectionné un délimiteur de texte, vous ne pouvez pas resélectionnez le **aucun** option. Tapez **Aucun** pour désélectionner l’identificateur de texte.  
  
 **Séparateur de lignes d'en-tête**  
 Choisissez dans la liste des séparateurs de lignes d'en-tête ou entrez le texte de séparation.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|La ligne d'en-tête est séparée par une combinaison retour chariot-saut de ligne.|  
|**{CR}**|La ligne d'en-tête est séparée par des retours chariot.|  
|**{LF}**|La ligne d'en-tête est séparée par des sauts de lignes.|  
|**Point-virgule {;}**|La ligne d'en-tête est séparée par des points-virgules.|  
|**Deux-points {:}**|La ligne d'en-tête est séparée par des deux-points.|  
|**Virgule {,}**|La ligne d'en-tête est séparée par des virgules.|  
|**Tabulation {t}**|La ligne d'en-tête est séparée par des tabulations.|  
|**Barre verticale {&#124;}**|La ligne d'en-tête est séparée par des barres verticales.|  
  
 **Lignes d'en-tête à ignorer**  
 Spécifiez le nombre de lignes à ignorer en haut du fichier, le cas échéant.  
  
 **Noms de colonnes dans la première ligne de données**  
 Spécifiez si la première ligne (après toutes les lignes ignorées) contient les noms de colonne.

## <a name="columns-page---format--delimited-source"></a>Page colonnes - Format = délimité (source)
 Dans la page **Colonnes**, vérifiez la liste des colonnes et les délimiteurs identifiés par l’Assistant. La capture d’écran suivante montre la page lorsque vous avez sélectionné **délimité** comme format de fichier plat.
 
![Fichier plat délimité, page colonnes](../../integration-services/import-export-data/media/flat-file-delimited-columns-page.jpg)

### <a name="options-to-specify-columns-page---format--delimited"></a>Options pour spécifier (**colonnes** page - Format = délimité)

 **Séparateur de lignes**  
 Effectuez une sélection dans la liste des séparateurs de lignes disponibles ou entrez le texte du séparateur.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les lignes sont séparées par une combinaison de retour chariot/saut de ligne.|  
|**{CR}**|Les lignes sont séparées par un retour chariot.|  
|**{LF}**|Les lignes sont séparées par un saut de ligne.|  
|**Point-virgule {;}**|Les lignes sont séparées par un point-virgule.|  
|**Deux-points {:}**|Les lignes sont séparées par un deux-points.|  
|**Virgule {,}**|Les lignes sont séparées par une virgule.|  
|**Tabulation {t}**|Les lignes sont séparées par une tabulation.|  
|**Barre verticale {&#124;}**|Les lignes sont séparées par une barre verticale.|  
  
 **Délimiteur de colonne**  
 Effectuez une sélection dans la liste des séparateurs de colonnes disponibles ou entrez le texte du séparateur.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les colonnes sont délimitées par une combinaison retour chariot-saut de ligne.|  
|**{CR}**|Les colonnes sont séparées par un retour chariot.|  
|**{LF}**|Les colonnes sont séparées par un saut de ligne.|  
|**Point-virgule {;}**|Les colonnes sont séparées par un point-virgule.|  
|**Deux-points {:}**|Les colonnes sont séparées par un deux-points.|  
|**Virgule {,}**|Les colonnes sont séparées par une virgule.|  
|**Tabulation {t}**|Les colonnes sont séparées par une tabulation.|  
|**Barre verticale {&#124;}**|Les colonnes sont séparées par une barre verticale.|  
  
 **Aperçu des lignes**  
 Affichez les données d'exemple dans le fichier plat, divisées en colonnes et en lignes à l'aide des options sélectionnées.  
 
 **Actualiser**  
 Affichez les résultats des modifications des séparateurs en cliquant sur **Actualiser**. Il ne devient visible qu'après avoir changé d'autres options de connexion.  
  
 **Réinitialiser les colonnes**  
 Restaurer les colonnes d’origine.  

## <a name="columns-page---format--fixed-width-source"></a>Page colonnes - Format = largeur fixe (source)
Dans la page **Colonnes**, vérifiez la liste des colonnes et les délimiteurs identifiés par l’Assistant. La capture d’écran suivante montre la page lorsque vous avez sélectionné **largeur fixe** comme format de fichier plat.
  
![Fichier plat, largeur, la page colonnes fixé](../../integration-services/import-export-data/media/flat-file-fixed-width-columns-page.jpg)

### <a name="options-to-specify-columns-page---format--fixed-width"></a>Options pour spécifier (**colonnes** page - Format = largeur fixe)

 **Police**  
 Sélectionnez la police d'affichage de l'aperçu des données.  
  
 **Colonnes de données sources**  
 Ajustez la largeur de la ligne en faisant glisser le marqueur de ligne rouge vertical, et celle des colonnes en cliquant sur la règle en haut de la fenêtre d'aperçu.  
  
 **Largeur de ligne**  
 Spécifiez la largeur de la ligne avant d'ajouter des séparateurs pour des colonnes distinctes. Vous pouvez également faire glisser la ligne rouge verticale dans la fenêtre d'aperçu pour marquer la fin de la ligne. La valeur de la largeur de ligne est automatiquement mise à jour.  
  
 **Réinitialiser les colonnes**  
 Restaurer les colonnes d’origine.  
  
## <a name="columns-page---format--ragged-right-source"></a>Page colonnes - Format = en drapeau à droite (source)
Dans la page **Colonnes**, vérifiez la liste des colonnes et les délimiteurs identifiés par l’Assistant. La capture d’écran suivante montre la page lorsque vous avez sélectionné **en drapeau à droite** comme format de fichier plat.

> [!NOTE]
> Dans les fichiers en drapeau à droite, chaque colonne a une largeur fixe, sauf la dernière qui est délimitée par le séparateur de lignes.  
 
![Fichier plat, en drapeau à droite, la page colonnes.](../../integration-services/import-export-data/media/flat-file-ragged-right-columns-page.jpg)

### <a name="options-to-specify-columns-page---format--ragged-right"></a>Options pour spécifier (**colonnes** page - Format = en drapeau à droite)
   
 **Police**  
 Sélectionnez la police d'affichage de l'aperçu des données.  
  
 **Colonnes de données sources**  
 Ajustez la largeur de la ligne en faisant glisser le marqueur de ligne rouge vertical, et celle des colonnes en cliquant sur la règle en haut de la fenêtre d'aperçu.  
  
 **Séparateur de lignes**  
 Effectuez une sélection dans la liste des séparateurs de lignes disponibles ou entrez le texte du séparateur.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**{CR}{LF}**|Les lignes sont séparées par une combinaison de retour chariot/saut de ligne.|  
|**{CR}**|Les lignes sont séparées par un retour chariot.|  
|**{LF}**|Les lignes sont séparées par un saut de ligne.|  
|**Point-virgule {;}**|Les lignes sont séparées par un point-virgule.|  
|**Deux-points {:}**|Les lignes sont séparées par un deux-points.|  
|**Virgule {,}**|Les lignes sont séparées par une virgule.|  
|**Tabulation {t}**|Les lignes sont séparées par une tabulation.|  
|**Barre verticale {&#124;}**|Les lignes sont séparées par une barre verticale.|  
  
 **Réinitialiser les colonnes**  
 Restaurer les colonnes d’origine.  

## <a name="advanced-page-source"></a>Page Avancé (source)
La page **Avancé** affiche des informations détaillées sur chaque colonne de la source de données, notamment son type de données et sa taille. L’écran suivant capture montre le **avancé** page pour la première colonne dans un fichier plat délimité.

![Page de fichier plat délimité, Avancé](../../integration-services/import-export-data/media/flat-file-delimited-advanced-page.jpg)

Dans la capture d’écran, notez que le **id** colonne, qui contient des nombres, a initialement un type de données de chaîne.

### <a name="options-to-specify-advanced-page"></a>Options pour spécifier (**avancé** page)

 **Configurez les propriétés de chaque colonne**  
 Dans le volet gauche, sélectionnez une colonne pour afficher ses propriétés dans celui de droite. Consultez le tableau suivant pour obtenir une description des propriétés de colonne. Certaines de ces propriétés sont configurables uniquement pour certains formats de fichier plat et pour les colonnes de certains types de données.  
  
|Propriété| Description|  
|--------------|-----------------|  
|**Nom**|Précisez un nom de colonne descriptif. Si vous n’entrez pas un nom, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée automatiquement un nom dans le format colonne 0, colonne 1 et ainsi de suite.|
|**ColumnDelimiter**|Sélectionnez un délimiteur de colonnes dans la liste des séparateurs de colonnes disponibles. Veillez à choisir un caractère de séparation qu'il est peu probable de rencontrer dans le texte. Cette valeur est ignorée dans le cas des colonnes à largeur fixe.<br /><br /> **{CR}{LF}**. Les colonnes sont délimitées par une combinaison retour chariot-saut de ligne.<br /><br /> **{CR}**. Les colonnes sont séparées par un retour chariot.<br /><br /> **{LF}**. Les colonnes sont séparées par un saut de ligne.<br /><br /> **Point-virgule {;}**. Les colonnes sont séparées par un point-virgule.<br /><br /> **Deux-points {:}**. Les colonnes sont séparées par un deux-points.<br /><br /> **Virgule {,}**. Les colonnes sont séparées par une virgule.<br /><br /> **Tabulation {t}**. Les colonnes sont séparées par une tabulation.<br /><br /> **Barre verticale {&#124;}**. Les colonnes sont séparées par une barre verticale.|
|**ColumnType**|Indique si la colonne est délimitée, si elle a une largeur fixe ou si elle présente un format en drapeau à droite. Cette propriété est en lecture seule. Les fichiers en drapeau à droite sont des fichiers dans lesquels chaque colonne a une largeur fixe, à l'exception de la dernière colonne. Un séparateur de lignes s'applique.|  
|**InputColumnWidth**|Spécifiez une valeur à stocker en tant que nombre d’octets ; pour les fichiers Unicode, cette valeur est un nombre de caractères. Cette valeur est ignorée dans le cas des colonnes délimitées.<br /><br /> **Remarque** : Dans le modèle objet, le nom de cette propriété est ColumnWidth.|
|**DataPrecision**|Spécifiez la précision des données numériques. La précision indique le nombre total de chiffres.|
|**DataScale**|Spécifiez l'échelle des données numériques. L'échelle est le nombre de décimales.|
|**DataType**|Sélectionnez un type de données dans la liste des types de données disponibles.<br/>Pour plus d'informations, consultez [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).|
|**OutputColumnWidth**|Indiquez une valeur spécifiant la largeur de colonne en nombre d'octets. Pour les fichiers Unicode, cette valeur correspond à un nombre de caractères. Dans la tâche de flux de données, cette valeur permet de définir la largeur de la colonne de sortie pour les fichiers plats sources. Dans le modèle objet, le nom de la propriété est MaximumWidth.|  
|**TextQualified**|Indique si les données de texte sont entourées par des caractères identificateurs de texte, tels que des caractères de guillemets.<br /><br /> True : les données texte du fichier plat sont qualifiées. False : les données texte du fichier plat ne sont pas qualifiées.|  
  
**Nouveau**  
 Ajoutez une nouvelle colonne en cliquant sur **Nouveau**. Par défaut, **ce bouton** ajoute une nouvelle colonne à la fin de la liste. Le bouton possède également les options ci-dessous, disponibles dans la liste déroulante.  
  
|Value|Description|  
|-----------|-----------------|  
|**Ajouter une colonne**|Ajoute une colonne à la fin de la liste.|  
|**Insérer avant**|Insère une nouvelle colonne avant la colonne sélectionnée.|  
|**Insérer après**|Insère une nouvelle colonne après la colonne sélectionnée.|  
  
 **Supprimer**  
 Sélectionnez une colonne, puis supprimez-la en cliquant sur **Supprimer**.  
  
 **Suggérer les types**  
 La boîte de dialogue **Suggérer les types de colonnes** permet d’évaluer des échantillons de données dans le fichier et d’obtenir des suggestions pour le type de données et la longueur de chaque colonne.  
 
Cliquez sur **Suggérer les types** pour afficher la boîte de dialogue **Suggérer les types de colonnes**. 

![Connexions de fichiers plats suggérer la boîte de dialogue types](../../integration-services/import-export-data/media/flat-file-connection-suggest.png)

Une fois que vous choisissez les options dans le **suggérer les Types de colonne** boîte de dialogue et cliquez sur **OK**, l’Assistant peut modifier les types de données de certaines colonnes.

La capture d’écran suivante montre que, après avoir cliqué sur **suggérer les types**, l’Assistant a détecté que le **id** colonne dans la source de données est en fait un nombre et non une chaîne de texte et a changé le type de données de la colonne à partir d’une chaîne en entier.

![Page Avancé de la connexion à un fichier plat (après)](../../integration-services/import-export-data/media/flat-file-connection-advanced-after.png)

Pour plus d’informations, consultez [suggérer référence de l’interface utilisateur de la colonne Types de boîte de dialogue](../../integration-services/connection-manager/suggest-column-types-dialog-box-ui-reference.md).

## <a name="preview-page-source"></a>Page d’aperçu (source)

Dans la page **Aperçu**, vérifiez que la liste des colonnes et que les exemples de données sont conformes à vos attentes.

![Fichier plat, page d’aperçu](../../integration-services/import-export-data/media/flat-file-preview-page.jpg)

### <a name="options-to-specify-preview-page"></a>Options pour spécifier (**aperçu** page)

 **Lignes de données à ignorer**  
 Indiquez le nombre de lignes qui doivent être ignorées à partir du début du fichier plat.  
  
 **Aperçu des lignes**  
 Affiche un échantillon de données du fichier plat, divisé en colonnes et en lignes en fonction des options que vous avez sélectionnées.
 
 **Actualiser**  
 Cliquez sur le bouton **Actualiser**pour visualiser l’effet obtenu en modifiant le nombre de lignes à ignorer. Il ne devient visible qu'après avoir changé d'autres options de connexion.  
 
Pour plus d’informations sur la page **Aperçu**, consultez la page [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Aperçu&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-preview-page.md) dans les informations de référence sur Integration Services.

## <a name="connect-to-a-flat-file-destination"></a>Se connecter à une destination de fichier plat
Pour une destination de fichier plat, il existe une seule page d’options, comme illustré dans la capture d’écran suivante. Cliquez sur Parcourir pour sélectionner le fichier, puis vérifiez les paramètres dans le **Format** section.

![Se connecter à la destination de fichier plat](../../integration-services/import-export-data/media/connect-to-flat-file-destination.jpg)

### <a name="options-to-specify-choose-a-destination-page"></a>Options pour spécifier (**choisir une Destination** page)

 **Nom de fichier**  
 Entrez le chemin d’accès et le nom du fichier plat.  
  
 **Parcourir**  
 Recherchez le fichier plat.  
  
 **Paramètres régionaux**  
 Spécifiez les paramètres régionaux pour fournir des informations spécifiques au langage pour le tri et pour les formats de date et d’heure.  
  
 **Unicode**  
 Spécifiez si le fichier utilise Unicode. Si vous utilisez Unicode, vous ne pouvez pas spécifier une page de codes.  
  
 **Page de codes**  
 Spécifiez la page de codes pour du texte non-Unicode.  
  
 **Format**  
 Déterminez si le fichier utilise délimité, largeur fixe ou en drapeau à la mise en forme à droite.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Délimité|Les colonnes sont séparées par des délimiteurs. Vous spécifiez le délimiteur sur le **colonnes** page.|  
|Largeur fixe|Les colonnes ont une largeur fixe.|  
|En drapeau à droite|Dans les fichiers en drapeau à droite, chaque colonne a une largeur fixe, sauf la dernière qui est délimitée par le séparateur de lignes.|  
  
 **Qualificateur de texte**  
 Spécifiez le qualificateur de texte, utilisée par le fichier. Par exemple, vous pouvez spécifier que les champs de texte soient placés entre guillemets. (Cette propriété s’applique uniquement aux fichiers de délimité.) 
  
> [!NOTE] 
> Après avoir sélectionné un délimiteur de texte, vous ne pouvez pas sélectionner à nouveau la **aucun** option. Tapez **Aucun** pour désélectionner l’identificateur de texte.  

## <a name="see-also"></a>Voir aussi
[Choisissez une Source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une Destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


