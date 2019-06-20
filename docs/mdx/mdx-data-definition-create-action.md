---
title: Instruction CREATE ACTION (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1e55a35144fce7b90cf4bb33cbbb82f26d8db62c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63233627"
---
# <a name="mdx-data-definition---create-action"></a>Définition de données MDX - CREATE ACTION


  Crée une action qui peut être associée à un cube, une dimension, une hiérarchie ou un objet subordonné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE ACTION CURRENTCUBE | Cube_Name  
   .Action_Name <action body>  
<action body> ::=   
FOR   
        CUBE   
    | Hierarchy_Name [MEMBERS]   
    | Level_Name [MEMBERS]   
    | CELLS   
    | SET }   
      AS 'MDX_Expression'   
        [, TYPE = '  
              { URL   
            | HTML   
            | STATEMENT   
               | DATASET   
            | ROWSET   
            | COMMANDLINE   
               | PROPRIETARY }   
         ']  
   [ , INVOCATION = 'INTERACTIVE | ON_OPEN | BATCH ' ]  
   [ , APPLICATION = String_Expression ]  
   [ , DESCRIPTION = String_Expression ]  
   [ , CAPTION = 'MDX_Expression' ]  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Chaîne valide qui précise le nom d'un cube.  
  
 *Nom de Action_*  
 Chaîne valide qui fournit le nom d'une action en cours de création.  
  
 *Nom de Hierarchy_*  
 Chaîne valide qui précise le nom d'une hiérarchie.  
  
 *Nom de Level_*  
 Chaîne valide qui précise le nom d'un niveau.  
  
 *Nom de Member_*  
 Chaîne valide qui précise un nom de membre ou une clé de membre.  
  
 *MDX_Expression*  
 Expression MDX valide.  
  
 *String_Expression*  
 Expression de chaîne valide.  
  
## <a name="remarks"></a>Notes  
 Les applications clientes peuvent créer et exécuter des actions qui ne sont pas sûres ; elles peuvent également utiliser des fonctions peu sûres. Pour éviter ces situations, utilisez la **des Options de sécurité** propriété. Pour plus d'informations, consultez la propriété Safety Options.  
  
> [!NOTE]  
>  Cette instruction est comprise pour des raisons de compatibilité descendante. Actions nouvelles dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], telles que les actions d’extraction ou un rapport, n’est pas pris en charge.  
  
## <a name="action-types"></a>Types d’action  
 Le tableau suivant décrit les différents types d’actions disponibles dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
|Type d'action|Description|  
|-----------------|-----------------|  
|**URL**|La chaîne d'action retournée est une URL qui doit être ouverte dans un navigateur Internet.<br /><br /> Remarque : Si cette action ne commence pas par `https://` ou `https://`, l’action n’est pas disponible dans le navigateur, sauf si **SafetyOptions** a la valeur **DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL**.|  
|**HTML**|La chaîne d'action retournée est un script HTML. Cette chaîne doit être enregistrée dans un fichier, qui devra être rendu à l'aide d'un navigateur Internet. Dans ce cas, un script entier peut être exécuté en tant que partie du fichier HTML généré.|  
|**INSTRUCTION**|La chaîne d’action retournée est une instruction qui doit être exécutée en définissant le **ICommand::SetText** méthode d’un objet de commande sur la chaîne et en appelant le **ICommand::Execute**(méthode). Si la commande échoue, un message d'erreur est retourné.|  
|**DATASET**|La chaîne d’action retournée est une instruction MDX qui doit être exécutée en définissant le **ICommand::SetText** méthode d’un objet de commande sur la chaîne et en appelant le **ICommand::Execute** (méthode). L’interface demandée ID (IID) doit être **IDataset**. Cette commande réussit si un dataset a été créé. L'application cliente doit autoriser l'utilisateur à parcourir le dataset retourné.|  
|**ENSEMBLE DE LIGNES**|Semblable à **DATASET**, mais au lieu de demander un IID de **IDataset**, l’application cliente doit demander un IID de **IRowset**. Cette commande réussit si un ensemble de lignes a été créé. L'application cliente doit autoriser l'utilisateur à parcourir l'ensemble de lignes retourné.|  
|**LIGNE DE COMMANDE**|L'application cliente doit exécuter la chaîne d'action. Cette chaîne est une ligne de commande.|  
|**PROPRIÉTAIRE**|Une application cliente ne doit pas afficher ni exécuter l'action, à moins d'avoir une connaissance personnalisée, non générique, de cette action spécifique. Les actions propriétaires ne sont pas retournées à l’application cliente, sauf si l’application cliente demande explicitement en définissant la restriction appropriée sur le **APPLICATION_NAME**.|  
  
## <a name="invocation-types"></a>Types d'invocations  
 Le tableau ci-dessous décrit les différents types d'invocations disponibles dans [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Le type d'invocation n'est utilisé que par l'application cliente pour déterminer à quel moment appeler l'action. Il ne détermine pas réellement le comportement d'invocation de l'action.  
  
|Type d'invocation|Description|  
|---------------------|-----------------|  
|**INTERACTIVE**|Cette action doit être appelée par l'application cliente via l'interaction de l'utilisateur.|  
|**ON_OPEN**|Cette action doit être appelée par l'application cliente lors de l'ouverture de l'objet cible. Ce type d'invocation n'est actuellement pas implémenté.|  
|**TRAITEMENT PAR LOTS**|Cette action doit être appelée par l'application cliente lorsque l'objet cible est impliqué dans une opération de traitement, comme déterminé par l'application cliente. Ce type d'invocation n'est actuellement pas implémenté.|  
  
### <a name="scope"></a>`Scope`  
 Chaque action est définie pour un cube spécifique et possède un nom unique dans ce cube. Une action peut avoir l'une des étendues répertoriées dans le tableau ci-après.  
  
 Étendue de cube   
 Pour les actions indépendantes de dimensions, membres ou cellules spécifiques ; par exemple : « Lancer l’émulation de terminal pour AS / 400 système de production ».  
  
 Étendue de dimension   
 Cette action s'applique à une dimension spécifique. Elle ne dépend pas d'une sélection spécifique de niveaux ou de membres.  
  
 Étendue de niveau   
 Cette action s'applique à un niveau de dimension spécifique. Elle ne dépend pas de la sélection spécifique d'un membre dans cette dimension.  
  
 Étendue de membre  
 Cette action s'applique aux membres d'un niveau spécifique.  
  
 Étendue de cellule   
 Cette action s'applique uniquement à des cellules spécifiques.  
  
 Étendue de jeu  
 Cette action s'applique uniquement à un jeu. Le nom, **ActionParameterSet**, son utilisation est réservée par l’application à l’intérieur de l’expression de l’action.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données MDX &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
