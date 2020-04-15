---
title: 'Annexe B : Tables de transition de l’État de l’ODBC (fr) Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- state transitions [ODBC]
- transitioning states [ODBC], about state transitions
- state transitions [ODBC], about state transitions
ms.assetid: 15088dbe-896f-4296-b397-02bb3d0ac0fb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db20c492ababbe6bf8f065fce88067c643f2694d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302883"
---
# <a name="appendix-b-odbc-state-transition-tables"></a>Annexe B : Tableaux des transitions d’état ODBC
Les tableaux de cette annexe montrent comment les fonctions d’ODBC causent des transitions de l’environnement, de la connexion, de l’énoncé et des états descripteur. L’état de l’environnement, de la connexion, de l’énoncé ou du descripteur dicte habituellement quand les fonctions qui utilisent le type correspondant de poignée (environnement, connexion, déclaration, ou descripteur) peuvent être appelées. L’environnement, la connexion, l’énoncé et les états descripteurs se chevauchent à peu près comme le montrent les illustrations suivantes. Par exemple, le chevauchement exact des états de connexion C5 et C6 et les états de déclaration S1 à S12 est dépendant des données, puisque les transactions commencent à différents moments sur différentes sources de données, et l’état descripteur D1i (descripteur implicitement attribué) dépend de l’état de la déclaration avec laquelle le descripteur est associé, tandis que l’état D1e (descripteur explicitement attribué) est indépendant de l’état de toute déclaration. Pour une description de chaque état, voir [Transitions de l’environnement](../../../odbc/reference/appendixes/environment-transitions.md), [transitions de connexion](../../../odbc/reference/appendixes/connection-transitions.md), [Transitions d’état](../../../odbc/reference/appendixes/statement-transitions.md), et [transitions descripteur](../../../odbc/reference/appendixes/descriptor-transitions.md), plus tard dans cette annexe.  
  
 Les états d’environnement et de connexion se chevauchent comme suit :  
  
 ![Chevauchement des états d'environnement et de connexion](../../../odbc/reference/appendixes/media/app01.gif "app01")  
  
 Les états de connexion et de déclaration se chevauchent comme suit :  
  
 ![Chevauchement des états de connexion et d'instruction](../../../odbc/reference/appendixes/media/app02.gif "app02")  
  
 L’énoncé et les états descripteur se chevauchent comme suit :  
  
 ![Chevauchement des états d'instruction et de descripteur](../../../odbc/reference/appendixes/media/app03.gif "app03")  
  
 Les états de connexion et descripteur se chevauchent comme suit :  
  
 ![Chevauchement des états de connexion et de descripteur](../../../odbc/reference/appendixes/media/app04.gif "app04")  
  
 Chaque entrée dans une table de transition peut être l’une des valeurs suivantes :  
  
-   **--**-L’état est inchangé après l’exécution de la fonction.  
  
-   **E**  

     **_n_** , **C_n_**, **S_n_**, ou **D_n_** - L’environnement, la connexion, la déclaration ou l’état descripteur se déplace à l’état spécifié.  
 
-   **(IH)** - Une poignée invalide a été transmise à la fonction. Si la poignée était une poignée nulle ou était une poignée valide du mauvais type - par exemple, une poignée de connexion a été adoptée lorsqu’une poignée de relevé était nécessaire - la fonction renvoie SQL_INVALID_HANDLE; sinon le comportement est indéfini et probablement fatal. Cette erreur n’est montrée que lorsque c’est le seul résultat possible d’appeler la fonction dans l’état spécifié. Cette erreur ne change pas l’état et est toujours détectée par le gestionnaire de conducteur, comme l’indiquent les parenthèses.  
  
-   **NS** - Prochain État. La transition de déclaration est la même que si la déclaration n’avait pas été passée par les états asynchrones. Supposons, par exemple, qu’une déclaration qui crée un ensemble de résultats entre dans l’état S11 de l’état S1 parce que **SQLExecDirect** est retournée SQL_STILL_EXECUTING. La notation NS dans l’état S11 signifie que les transitions pour la déclaration sont les mêmes que celles pour une déclaration dans l’état S1 qui crée un ensemble de résultats. Si **SQLExecDirect** renvoie une erreur, la déclaration demeure dans l’état S1; s’il réussit, la déclaration passe à l’état S5; s’il a besoin de données, l’instruction passe à l’état S8; et s’il est toujours en cours d’exécution, il reste dans l’état S11.  

-   **_XXXXX_** ou **(*XXXXX*)** - Un SQLSTATE qui est lié à la table de transition; Les SQLSTATEs détectées par le gestionnaire de conducteur sont enfermées entre parenthèses. La fonction est retournée SQL_ERROR et le SQLSTATE spécifié, mais l’état ne change pas. Par exemple, si **SQLExecute** est appelé avant **SQLPrepare**, il retourne SQLSTATE HY010 (erreur de séquence de fonction).  

> [!NOTE]  
>  Les tableaux ne montrent pas d’erreurs sans rapport avec les tables de transition qui ne changent pas l’état. Par exemple, lorsque **SQLAllocHandle** est appelé dans l’état de l’environnement E1 et retourne SQLSTATE HY001 (erreur d’allocation de mémoire), l’environnement reste dans l’état E1; ce n’est pas indiqué dans le tableau de transition de l’environnement pour **SQLAllocHandle**.  
  
 Si l’environnement, la connexion, l’énoncé ou le descripteur peuvent se déplacer vers plus d’un état, chaque état possible est affiché et une ou plusieurs notes de bas de page expliquent les conditions dans lesquelles chaque transition a lieu. Les notes de bas de page suivantes peuvent apparaître dans n’importe quel tableau.  
  
|Note|Signification|  
|--------------|-------------|  
|b|Avant ou après. Le curseur a été positionné avant le début de l’ensemble de résultat ou après la fin de l’ensemble de résultat.|  
|c|Fonction actuelle. La fonction actuelle s’exécutait asynchronement.|  
|d|Besoin de données. La fonction est retournée SQL_NEED_DATA.|  
|e|. La fonction est retournée SQL_ERROR.|  
|i|Ligne invalide. Le curseur a été positionné sur une rangée dans l’ensemble de résultat et soit la ligne avait été supprimée ou une erreur s’était produite dans une opération sur la rangée. Si le tableau d’état de la ligne existait, la valeur du tableau d’état de la ligne pour la rangée était SQL_ROW_DELETED ou SQL_ROW_ERROR. (Le tableau d’état de la ligne est indiqué par l’attribut de l’énoncé SQL_ATTR_ROW_STATUS_PTR.)|  
|nf|Introuvable. La fonction est retournée SQL_NO_DATA. Cela ne s’applique pas lorsque **SQLExecDirect**, **SQLExecute**, ou **SQLParamData** retourne SQL_NO_DATA après avoir exécuté une mise à jour recherchée ou supprimer la déclaration.|  
|np|Pas préparé. La déclaration n’a pas été préparée.|  
|nr|Aucun résultat. L’énoncé n’établira pas ou n’a pas créé d’ensemble de résultats.|  
|o|Autre fonction. Une autre fonction a été l’exécution asynchrone.|  
|p|Préparé. La déclaration a été préparée.|  
|r|Résultats. L’énoncé créera ou créera un ensemble de résultats (peut-être vide).|  
|s|Réussite. La fonction est retournée SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS.|  
|v|Ligne valide. Le curseur a été positionné sur une rangée dans l’ensemble de résultat, et la rangée avait été insérée avec succès, mis à jour avec succès, ou une autre opération sur la rangée avait été complétée avec succès. Si le tableau d’état de la ligne existait, la valeur du tableau d’état de la rangée pour la rangée était SQL_ROW_ADDED, SQL_ROW_SUCCESS ou SQL_ROW_UPDATED. (Le tableau d’état de la ligne est indiqué par l’attribut de l’énoncé SQL_ATTR_ROW_STATUS_PTR.)|  
|x|En cours d'exécution. La fonction est retournée SQL_STILL_EXECUTING.|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
 Dans cet exemple, la ligne dans la table de transition de l’état de l’environnement pour **SQLFreeHandle** lorsque *HandleType* est SQL_HANDLE_ENV est le suivant.  
  
|E0 (E0)<br /><br /> Non alloué|E1<br /><br /> Allocated|E2<br /><br /> Connexion|  
|------------------------|----------------------|-----------------------|  
|(IH)|E0 (E0)|(HY010)|  
  
 Si **SQLFreeHandle** est appelé dans l’état de l’environnement E0 avec *HandleType* mis à SQL_HANDLE_ENV, le gestionnaire de conducteur retourne SQL_INVALID_HANDLE. S’il est appelé dans l’état E1 avec *HandleType* mis à SQL_HANDLE_ENV, l’environnement se déplace à l’état E0 si la fonction réussit et reste en état E1 si la fonction échoue. S’il est appelé en état E2 avec *HandleType* mis à SQL_HANDLE_ENV, le Driver Manager retourne toujours SQL_ERROR et SQLSTATE HY010 (erreur de séquence de fonction) et l’environnement reste en état E2.  
  
 Pour comprendre les tableaux de transition de l’État, il est nécessaire de comprendre à quel élément (environnement, connexion, déclaration ou descripteur) ils se réfèrent. Supposons qu’une fonction accepte la poignée d’un élément de type X. La table de transition de l’état X pour cette fonction décrit comment l’appel de la fonction, avec la poignée d’un élément de type X, affecte cet élément. Par exemple, **SQLDisconnect** accepte une poignée de connexion. Le tableau de transition de l’état de connexion pour **SQLDisconnect** décrit comment **SQLDisconnect** affecte l’état de la connexion pour laquelle il est appelé.  
  
 Supposons qu’une fonction accepte la poignée d’un élément de type Y, où Y n’est pas égal à X. Le tableau de transition de l’état X pour cette fonction décrit comment l’appel de la fonction, avec une poignée de type X qui est associé à l’élément de type Y, affecte l’élément de type Y. Par exemple, le tableau de transition de l’état de déclaration pour **SQLDisconnect** décrit comment **SQLDisconnect** affecte l’état d’une déclaration lorsqu’il est appelé avec la poignée de la connexion avec laquelle la déclaration est associée.  
  
 Cette annexe contient les sujets suivants.  
  
-   [Transitions d’environnement](../../../odbc/reference/appendixes/environment-transitions.md)  
  
-   [Transitions de connexion](../../../odbc/reference/appendixes/connection-transitions.md)  
  
-   [Transitions d’instruction](../../../odbc/reference/appendixes/statement-transitions.md)  
  
-   [Transitions de descripteur](../../../odbc/reference/appendixes/descriptor-transitions.md)
