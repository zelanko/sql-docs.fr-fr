---
title: Paramètres régionaux non-système
description: Découvrez comment les différents paramètres régionaux dans Linux et macOS affectent les pilotes Microsoft SQL Server pour PHP
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- locale, linux, macOS, system
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 303037729164d4165fc106529a901b58d4d049f4
ms.sourcegitcommit: d1051f05a7db81ec62d9785bb6af572408f3d4e0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88680524"
---
# <a name="non-system-locale-settings"></a>Paramètres régionaux non-système
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette section s’applique uniquement aux utilisateurs Linux et macOS, en particulier ceux qui traitent plusieurs paramètres régionaux dans leurs applications PHP.

Par défaut, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] prend la variable d’environnement `LC_ALL` définie dans le système et remplace toutes les autres catégories `LC_xxx` (sauf peut-être `$LANG` ou `$LANGUAGE` dans certaines circonstances), en affectant le séparateur de milliers, le caractère virgule décimale, le jeu de caractères, le mois, les noms de jours, les messages d’application tels que les messages d’erreur, le symbole monétaire, etc.

À partir de la version 5.8.0, les utilisateurs peuvent configurer les paramètres de localisation à l’aide du fichier php.ini, comme indiqué dans les exemples ci-dessous.

## <a name="set-locale-info-using-the-sqlsrv-driver"></a>Définir des paramètres régionaux à l’aide du pilote SQLSRV  
Ajoutez ce qui suit à la fin de votre fichier php.ini :
  
```  
[sqlsrv]  
sqlsrv.SetLocaleInfo = <option>
```  
  
## <a name="set-locale-info-using-the-pdo_sqlsrv-driver"></a>Définir des paramètres régionaux à l’aide du pilote PDO_SQLSRV  
Ajoutez ce qui suit à la fin de votre fichier php.ini :
  
```  
[pdo_sqlsrv]  
pdo_sqlsrv.set_locale_info = <option>
```  
  
Les valeurs suivantes peuvent déterminer l'**option** :  
  
|Option|Description du comportement|
|---------|---------------|
|0|Le pilot ignore les paramètres régionaux du système.|
|1|Le pilote lit la variable LC_CTYPE.|
|2|Le pilote lit la variable LC_ALL (valeur par défaut).|
  

La catégorie `LC_CTYPE` détermine les règles de gestion des caractères, qui régissent l’interprétation des séquences d’octets des caractères de données de texte, la classification des caractères et le comportement des classes de caractères. Il contrôle la reconnaissance des caractères en majuscule et en minuscule, des caractères alphabétiques et non alphabétiques et ainsi de suite.

### <a name="explanation"></a>Explication

1. Option 0 -- utilisez cette option lorsque vous ne souhaitez pas modifier les paramètres régionaux de l’application.

1. Option 1 -- permet de définir uniquement la valeur système de `LC_CTYPE` sans affecter les autres catégories `LC_xxx`.

1. Option 2 -- Utilisez `LC_ALL` pour remplacer toutes les catégories `LC_xxx`, affectant l’application php et ses extensions.

Si les paramètres régionaux d’un script PHP ne sont pas les mêmes que ceux du système, vous devrez peut-être spécifier les paramètres régionaux dans le ou les scripts PHP en appelant la fonction intégrée php [setlocale](https://www.php.net/manual/en/function.setlocale.php). 

Par exemple, si la valeur par défaut du système est `en_US.UTF-8` mais que le script php utilise `de_DE.UTF-8`, appelez la fonction php `setlocale()` de manière appropriée.

Pour l’option 2, indiquez les paramètres régionaux souhaités dans vos scripts PHP uniquement s’ils sont différents de la variable `LC_ALL`.

> [!NOTE]
> Si rien n’est défini dans php.ini, la valeur par défaut actuelle consiste à remplacer tous les autres paramètres régionaux en fonction de `LC_ALL`, qui sera **déconseillé**. Dans un avenir proche, la valeur par défaut sera d’ignorer les paramètres régionaux du système. Ainsi, les utilisateurs devront modifier le fichier php.ini en conséquence s’ils souhaitent conserver le comportement actuel.

Si les pilotes sqlsrv et pdo_sqlsrv sont tous deux activés, il n’est pas recommandé de définir des options différentes pour les deux pilotes.
