---
title: SET COLLATE, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set collate command [ODBC]
ms.assetid: 00efbcd4-fea8-4061-86a5-82de413cb753
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 372d3b2df79d66084f5599b4ac098b8c273ee78a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801953"
---
# <a name="set-collate-command"></a>SET COLLATE, commande
Spécifie une séquence de classement pour les champs caractères dans les opérations de tri et de l’indexation suivantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET COLLATE TO cSequenceName  
```  
  
## <a name="arguments"></a>Arguments  
 *cSequenceName*  
 Spécifie une séquence de classement. Les options de séquence de classement disponibles sont décrites dans le tableau suivant.  
  
|Options|Langue|  
|-------------|--------------|  
|NÉERLANDAIS|Néerlandais|  
|GENERAL|Anglais, Français, allemand, Espagnol moderne, portugais et autres langues d’Europe occidentale|  
|ALLEMAND|Commande allemand annuaire téléphonique (DIN)|  
|ISLANDE|Islandais|  
|MACHINE|Machine (la séquence de classement par défaut pour les versions antérieures de FoxPro)|  
|NORDAN|Norvégien, danois|  
|ESPAGNOL|Espagnol traditionnel|  
|SWEFIN|Suédois, finnois|  
|UNIQWT|Poids unique|  
  
> [!NOTE]  
>  Lorsque vous spécifiez l’option espagnole, *ch* est une lettre unique qui effectue un tri entre *c* et *d*, et *ll* trie entre  *l* et *m*.  
  
 Si vous spécifiez une option de séquence de classement en tant que caractère littéral chaîne, veillez à placer l’option de guillemets :  
  
```  
SET COLLATE TO "SWEFIN"  
```  
  
 MACHINE est l’option de séquence de classement par défaut et que les utilisateurs de Xbase séquence sont familiarisés avec. Caractères sont classés comme ils apparaissent dans la page de codes actuelle.  
  
 GÉNÉRAL peut être préférable pour les utilisateurs des États-Unis et Europe de l’ouest. Caractères sont classés comme ils apparaissent dans la page de codes actuelle. Dans les versions de FoxPro antérieurs à 2.5, index peuvent avoir été créés à l’aide de la **supérieur**() ou **inférieure**fonctions () pour convertir les champs de caractère à un incident cohérent. Dans les versions de FoxPro 2.5 au plus tard, vous pouvez spécifier l’option de séquence de classement général et omettez la **supérieur**conversion de ().  
  
 Si vous spécifiez une option de séquence de classement autre que l’ordinateur et si vous créez un fichier .idx, un .idx compact est toujours créé.  
  
 Utilisez SET("COLLATE") pour retourner la séquence de classement actuel.  
  
 Vous pouvez spécifier un ordre de tri pour une source de données à l’aide de la [boîte de dialogue d’installation ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) ou en utilisant le mot clé Collate dans votre chaîne de connexion avec [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md). Cela est identique à l’émission de la commande suivante :  
  
```  
SET COLLATE TO cSequenceName  
```  
  
## <a name="remarks"></a>Notes  
 Définissez COLLATE vous permet d’ordonner les tables contenant les caractères accentués pour toutes les langues prises en charge. Modification du paramètre de valeur COLLATE n’affecte pas l’ordre de tri des index précédemment ouverts. Visual FoxPro gère automatiquement les index existants, en offrant la flexibilité nécessaire pour créer différents types d’index, même pour le même champ.  
  
 Par exemple, si un index est créé avec la valeur COLLATE général la valeur et le paramètre de valeur COLLATE est changé ultérieurement vers l’espagnol, l’index conserve la séquence de classement général.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’ODBC pour Visual FoxPro, boîte de dialogue](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
