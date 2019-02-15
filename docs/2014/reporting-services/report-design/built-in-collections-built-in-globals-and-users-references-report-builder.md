---
title: Références à des champs Globals et Users prédéfinis (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5f5e1149-c967-454d-9a63-18ec4a33d985
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e41b76481748175a68b4a0a0a4877c7c17147788
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56288567"
---
# <a name="built-in-globals-and-users-references-report-builder-and-ssrs"></a>Références à des champs Globals et Users prédéfinis (Générateur de rapports et SSRS)
  La collection de champs prédéfinis, qui inclut à la fois les collections `Globals` et `User`, représente les valeurs globales fournies par Reporting Services lorsqu'un rapport est traité. La collection `Globals` fournit des valeurs, telles que le nom du rapport, l'heure de début du traitement du rapport et les numéros des pages actuelles pour l'en-tête ou le pied de page du rapport. La collection `User` fournit les paramètres d'identificateur d'utilisateur et de langue. Ces valeurs peuvent être utilisées dans les expressions pour filtrer les résultats dans un rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-globals-collection"></a>Utilisation de la collection Globals  
 La collection `Globals` comprend les variables globales du rapport. Dans l’aire de conception, ces variables apparaissent avec le préfixe & (esperluette), par exemple, `[&ReportName]`. Le tableau ci-dessous décrit les membres de la collection `Globals`.  
  
|**Membre**|**Type**|**Description**|  
|----------------|--------------|---------------------|  
|ExecutionTime|`DateTime`|Date et heure du début de l'exécution du rapport.|  
|PageNumber|`Integer`|Numéro de page actuel relatif aux sauts de page qui réinitialisent le nombre de pages. Au début du traitement des rapports, la valeur initiale est 1. Le numéro de page est incrémenté pour chaque page rendue.<br /><br /> Pour numéroter les pages au sein des sauts de page pour un rectangle, une région de données, un groupe de régions de données ou une carte, dans la propriété PageBreak, la valeur est la propriété ResetPageNumber `True`. Non pris en charge dans la hiérarchie des groupes de colonnes de tableau matriciel.<br /><br /> PageNumber peut uniquement être utilisé dans une expression figurant dans un en-tête ou un pied de page.|  
|ReportFolder|`String`|Chemin d'accès complet au dossier contenant le rapport. Ce chemin n'inclut pas l'URL du serveur de rapports.|  
|ReportName|`String`|Nom du rapport tel qu'il est stocké dans la base de données du serveur de rapports.|  
|ReportServerUrl|`String`|URL du serveur de rapports sur lequel le rapport est en cours d'exécution.|  
|TotalPages|`Integer`|Nombre total de pages par rapport aux sauts de page qui réinitialisent PageNumber. Si aucun saut de page n’est défini, cette valeur est identique à celle de OverallTotalPages.<br /><br /> TotalPages peut uniquement être utilisé dans une expression figurant dans un en-tête ou un pied de page.|  
|PageName|`String`|Nom de la page. Au début du traitement d’un rapport, la valeur initiale est celle définie pour la valeur de la propriété de rapport InitialPageName. À mesure que chaque élément de rapport est traité, cette valeur est remplacée par la valeur correspondante de PageName d’un rectangle, d’une région de données, d’un groupe de régions de données ou d’une carte. Non pris en charge dans la hiérarchie des groupes de colonnes de tableau matriciel.<br /><br /> PageName peut uniquement être utilisé dans une expression figurant dans un en-tête ou un pied de page.|  
|OverallPageNumber|`Integer`|Numéro de la page actuelle pour le rapport entier. Cette valeur n’est pas affectée par ResetPageNumber.<br /><br /> OverallPageNumber peut uniquement être utilisé dans une expression figurant dans un en-tête ou un pied de page.|  
|OverallTotalPages|`Integer`|Nombre total de pages pour le rapport entier. Cette valeur n’est pas affectée par ResetPageNumber.<br /><br /> OverallTotalPages peut uniquement être utilisé dans une expression figurant dans un en-tête ou un pied de page.|  
|RenderFormat|`RenderFormat`|Informations sur la demande de rendu actuelle.<br /><br /> Pour plus d'informations, consultez « RenderFormat » dans la section suivante.|  
  
 Les membres de la collection `Globals` retournent un type Variant. Si vous souhaitez utiliser un membre de cette collection dans une expression nécessitant un type de données spécifique, vous devez en premier lieu effectuer le cast de la variable. Par exemple, pour convertir le type Variant de temps d'exécution en format de date, utilisez `=CDate(Globals!ExecutionTime)`. Pour plus d’informations, consultez [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
### <a name="renderformat"></a>RenderFormat  
 Le tableau suivant décrit les membres de `RenderFormat`.  
  
|Membre|Type|Description|  
|------------|----------|-----------------|  
|Créer une vue d’abonnement|`String`|Nom du convertisseur tel qu'il a été inscrit dans le fichier de configuration RSReportServer.<br /><br /> Disponible pendant des parties spécifiques du cycle de traitement/rendu des rapports.|  
|IsInteractive|`Boolean`|Indique si la demande de rendu actuelle utilise un format de rendu interactif.|  
|DeviceInfo|Collection nom/valeur en lecture seule|Paires clé/valeur pour les paramètres deviceinfo de la demande de rendu actuelle.<br /><br /> Les valeurs de chaîne peuvent être spécifiées en utilisant la clé ou un index dans la collection.|  
  
### <a name="examples"></a>Exemples  
 Les exemples suivants montrent comment utiliser une référence à la collection `Globals` dans une expression :  
  
-   Cette expression, placée dans une zone de texte dans le pied de page d'un rapport, indique le numéro de la page actuelle ainsi que le nombre total de pages du rapport :  
  
     `=Globals.PageNumber & " of " & Globals.TotalPages`  
  
-   Cette expression fournit le nom du rapport ainsi que l'heure de son exécution. L'heure est mise en forme avec la chaîne de mise en forme [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] pour la date courte :  
  
     `=Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")`  
  
-   Cette expression, placée dans la boîte de dialogue **Visibilité de la colonne** pour une colonne sélectionnée, affiche la colonne uniquement lorsque le rapport est exporté vers Excel. Dans les autres cas, cette colonne est masquée.  
  
     `EXCELOPENXML` fait référence au format Excel inclus dans Office 2007. `EXCEL` fait référence au format Excel inclus dans Office 2003.  
  
     `=IIF(Globals!RenderFormat.Name = "EXCELOPENXML" OR Globals!RenderFormat.Name = "EXCEL", false, true)`  
  
## <a name="using-the-user-collection"></a>Utilisation de la collection User  
 La collection `User` contient des données relatives à l'utilisateur qui exécute le rapport. Vous pouvez utiliser cette collection pour filtrer les données qui apparaissent dans un rapport, par exemple pour montrer uniquement les données de l'utilisateur actuel ou inclure l'ID utilisateur dans un titre de rapport. Dans l’aire de conception, ces variables apparaissent avec le préfixe & (esperluette), par exemple, `[&UserID]`.  
  
 Le tableau ci-dessous décrit les membres de la collection `User`.  
  
|**Membre**|**Type**|**Description**|  
|----------------|--------------|---------------------|  
|`Language`|`String`|Langue de l'utilisateur qui exécute le rapport. Par exemple, `en-US`.|  
|`UserID`|`String`|Identificateur de l'utilisateur qui exécute le rapport. Si vous utilisez l'authentification Windows, cette valeur correspond au compte de domaine de l'utilisateur actuel. La valeur est déterminée par l'extension de sécurité de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , qui peut utiliser l'authentification Windows ou une authentification personnalisée.|  
  
 Pour plus d’informations sur la prise en charge de plusieurs langues dans un rapport, consultez « Considérations sur la conception de la solution pour les déploiements multilingues ou globaux » dans la section [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la [documentation en ligne SQL Server](https://go.microsoft.com/fwlink/?LinkId=120955).  
  
### <a name="using-locale-settings"></a>Utilisation des paramètres régionaux  
 Vous pouvez utiliser des expressions pour faire référence aux paramètres régionaux sur un ordinateur client au moyen de la valeur `User.Language` pour déterminer l'aspect d'un rapport pour l'utilisateur. Par exemple, vous pouvez créer un rapport qui utilise une expression de requête différente en fonction de la valeur d'un paramètre régional. La requête peut changer de façon à récupérer des informations localisées, provenant d'une colonne différente selon la langue indiquée en retour. Vous pouvez également utiliser une expression dans les paramètres de langue du rapport ou des éléments de rapport basés sur cette variable.  
  
> [!NOTE]  
>  S'il est possible de modifier les paramètres de langue d'un rapport, vous devez toutefois faire preuve de prudence car cela peut entraîner des problèmes d'affichage. Ainsi, un tel changement peut entraîner la modification du format de date du rapport, mais aussi du format de la devise. Si un processus de conversion de devise n'a pas été mis en place, cela peut provoquer l'affichage de symboles de devises incorrects dans le rapport. Pour éviter un tel problème, définissez les informations de langue sur les éléments individuels à modifier ou attribuez à l'élément comportant les données monétaires une langue spécifique.  
  
### <a name="identifying-userid-for-snapshot-or-history-reports"></a>Identification de l'ID utilisateur pour les rapports d'historique ou d'instantané  
 Dans certains cas, les rapports qui contiennent la variable *User!UserID* ne parviennent pas à afficher les données de rapport spécifiques de l’utilisateur qui affiche le rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Boîte de dialogue Expression &#40;Générateur de rapports&#41;](../expression-dialog-box-report-builder.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Mise en forme des nombres et des dates &#40;Générateur de rapports et SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)  
  
  
