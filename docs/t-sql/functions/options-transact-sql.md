---
title: '@@OPTIONS (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@OPTIONS'
- '@@OPTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- SET statement, current SET options
- '@@OPTIONS function'
- current SET options
ms.assetid: 3d5c7f6e-157b-4231-bbb4-4645a11078b3
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 9480ffeffa83650b5cf44ad51547c36d5563b13b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40options-transact-sql"></a>& #x 40 ; & #x 40 ; OPTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne des informations sur les options SET actuelles.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
@@OPTIONS  
```  
  
## <a name="return-types"></a>Types de retour  
 **entier**  
  
## <a name="remarks"></a>Notes  
 Les options peuvent provenir de l’utilisation de la **définir** commande ou à partir de la **option sp_configure user options** valeur. Configuré avec des valeurs de session le **définir** commande remplacement le **sp_configure** options. De nombreux outils (tels que [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]) configurent automatiquement les options de définition. Chaque utilisateur possède un @@OPTIONS (fonction) qui représente la configuration.  
  
 Vous pouvez modifier les options linguistiques et de traitement des requêtes pour une session utilisateur spécifique à l'aide de l'instruction SET. **@@OPTIONS**  peut détecter uniquement les options qui ont pour valeur ON ou OFF.  
  
 Le **@@OPTIONS**  fonction retourne une image bitmap des options, converti en entier base 10 (décimal). Les paramètres de bit sont stockés dans les emplacements décrits dans une table dans la rubrique [configurer l’Option de Configuration de serveur user options](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md).  
  
 Pour décoder le **@@OPTIONS**  valeur, convertissez l’entier retourné par **@@OPTIONS**  en binaire, puis recherchez les valeurs de la table de [configurer l’Option de Configuration de serveur user options](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md). Par exemple, si `SELECT @@OPTIONS;` retourne la valeur `5496`, utilisez la calculatrice de programmation Windows (**calc.exe**) pour convertir la valeur décimale `5496` en binaire. Le résultat est `1010101111000`. Les caractères situés les plus à droite (binaire 1, 2 et 4) sont 0, ce qui indique que les trois premiers éléments de la table sont désactivés. Consultation de la table, vous voyez que celles sont **DISABLE_DEF_CNST_CHK** et **IMPLICIT_TRANSACTIONS**, et **CURSOR_CLOSE_ON_COMMIT**. L’élément suivant (**ANSI_WARNINGS** dans les `1000` position) se trouve sur. Continuer à travailler à gauche si le bitmap et vers le bas dans la liste des options. Lorsque les options de la plus à gauche sont 0, elles sont tronquées par la conversion de type. Le bitmap `1010101111000` est en fait `001010101111000` et représente les 15 options.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-demonstration-of-how-changes-affect-behavior"></a>A. Démonstration de l'impact des modifications sur le comportement  
 L’exemple suivant montre la différence de comportement de concaténation avec deux paramètres différents de la **CONCAT_NULL_YIELDS_NULL** option.  
  
```  
SELECT @@OPTIONS AS OriginalOptionsValue;  
SET CONCAT_NULL_YIELDS_NULL OFF;  
SELECT 'abc' + NULL AS ResultWhen_OFF, @@OPTIONS AS OptionsValueWhen_OFF;  
  
SET CONCAT_NULL_YIELDS_NULL ON;  
SELECT 'abc' + NULL AS ResultWhen_ON, @@OPTIONS AS OptionsValueWhen_ON;  
```  
  
### <a name="b-testing-a-client-nocount-setting"></a>B. Test du paramètre NOCOUNT d'un client  
 L’exemple suivant définit `NOCOUNT``ON` , puis teste la valeur de `@@OPTIONS`. Le `NOCOUNT``ON` option empêche le message concernant le nombre de lignes affectées d’être renvoyé au client demandeur pour chaque instruction dans une session. La fonction `@@OPTIONS` a pour valeur `512` (0x0200). Ceci représente l'option NOCOUNT. Cet exemple teste si l'option NOCOUNT est activée sur le client. Vous pouvez vous en servir pour rechercher les différences de performances sur un ordinateur client.  
  
```  
SET NOCOUNT ON  
IF @@OPTIONS & 512 > 0   
RAISERROR ('Current user has SET NOCOUNT turned on.', 1, 1)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de configuration &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Configurer l’option de configuration du serveur user options](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md)  
  
  

