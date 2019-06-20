---
title: Le fichier Schema.ini (pilote de fichier texte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- schema.ini file [ODBC]
- text file driver [ODBC], schema.ini file
ms.assetid: 0c4625c4-c730-4984-b430-9051b7bc0451
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 708442d30b571f165f7f9d70f346a958764316d0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127906"
---
# <a name="schemaini-file-text-file-driver"></a>Fichier Schema.ini (pilote du fichier texte)
Lorsque le pilote de texte est utilisé, le format du fichier texte est déterminé à l’aide d’un fichier d’informations de schéma. Le fichier d’informations de schéma est toujours nommé Schema.ini et toujours conservé dans le même répertoire que la source de données de texte. Le fichier d’informations de schéma fournit la méthode IISAM avec des informations sur le format général du fichier, le nom de colonne et les informations de type de données et plusieurs autres caractéristiques de données. Un fichier Schema.ini est toujours requis pour accéder aux données de longueur fixe. Vous devez utiliser un fichier Schema.ini lorsque votre table de texte contient la date/heure, devise, ou données Decimal ou à tout moment que vous souhaitez contrôler davantage la gestion des données dans la table.  
  
> [!NOTE]  
>  Le texte ISAM obtiendra des valeurs initiales à partir du Registre et non à partir de Schema.ini. Le même format de fichier par défaut s’applique à toutes les nouvelles tables de données de texte. Tous les fichiers qui ont été créés par l’instruction CREATE TABLE héritent de ces mêmes valeurs de format par défaut, qui sont définis en sélectionnant les valeurs de format de fichier dans le **définition du Format texte** boîte de dialogue avec \<par défaut > choisi dans le  **Tables** liste. Si les valeurs dans le Registre diffèrent des valeurs dans Schema.ini, les valeurs dans le Registre sont remplacées par les valeurs de Schema.ini.  
  
## <a name="understanding-schemaini-files"></a>Présentation des fichiers Schema.ini  
 Fichiers Schema.ini fournissent des informations de schéma sur les enregistrements dans un fichier texte. Chaque entrée Schema.ini spécifie une des cinq caractéristiques de la table :  
  
-   Le nom du fichier texte  
  
-   Le format de fichier  
  
-   Les noms de champs, les largeurs et les types  
  
-   Le jeu de caractères  
  
-   Conversions de types de données spéciaux  
  
 Les sections suivantes décrivent ces caractéristiques.  
  
## <a name="specifying-the-file-name"></a>En spécifiant le nom de fichier  
 La première entrée de Schema.ini est toujours le nom du fichier texte source placée entouré crochets. L’exemple suivant illustre l’entrée pour le fichier Sample.txt :  
  
```  
[Sample.txt]  
```  
  
## <a name="specifying-the-file-format"></a>Spécification du Format de fichier  
 Le **Format** option dans Schema.ini spécifie le format du fichier texte. Le Text IISAM capable de lire le format automatiquement à partir des fichiers plus délimitée par des caractères. Vous pouvez utiliser n’importe quel caractère unique comme un délimiteur dans le fichier à l’exception du guillemet double («). Le **Format** paramètre dans Schema.ini remplace le paramètre dans le Registre Windows, fichier par fichier. Le tableau suivant répertorie les valeurs valides pour le **Format** option.  
  
|Spécificateur de format|Format de table|Instruction Schema.ini Format|  
|----------------------|------------------|---------------------------------|  
|**Délimité par des tabulations**|Les champs dans le fichier sont délimités par des tabulations.|Format=TabDelimited|  
|**Délimité CSV**|Les champs dans le fichier sont délimités par des virgules (CSV).|Format = CSVDelimited|  
|**Délimité personnalisée**|Champs dans le fichier sont délimités par n’importe quel caractère que vous choisissez d’entrer dans la boîte de dialogue. Tout sauf les guillemets doubles (") sont autorisées, y compris vide.|Format = délimité (*caractère personnalisé*)<br /><br /> -ou-<br /><br /> Sans délimiteur spécifié :<br /><br /> Format=Delimited( )|  
|**Longueur fixe**|Les champs dans le fichier sont de longueur fixe.|Format=FixedLength|  
  
## <a name="specifying-the-fields"></a>Spécification des champs  
 Vous pouvez spécifier des noms de champs dans un fichier texte délimité par des caractères de deux manières :  
  
-   Inclure les noms de champs dans la première ligne de la table et définissez **ColNameHeader** à **True.**  
  
-   Spécifiez chaque colonne par un nombre et désigner la colonne nom et type de données.  
  
 Vous devez spécifier chaque colonne en nombre et désigner le nom de colonne, type de données et la largeur pour les fichiers de longueur fixe.  
  
> [!NOTE]  
>  Le **ColNameHeader** définition dans les remplacements de Schema.ini le **FirstRowHasNames** définition dans le Registre Windows, fichier par fichier.  
  
 Vous pouvez également déterminer les types de données des champs. Utilisez le **MaxScanRows** option pour indiquer le nombre de lignes doit être analysé pour déterminer les types de colonnes. Si vous définissez **MaxScanRows** à 0, la totalité du fichier est analysé. Le **MaxScanRows** paramètre dans Schema.ini remplace le paramètre dans le Registre Windows, fichier par fichier.  
  
 L’entrée suivante indique que Microsoft Jet doit utiliser les données dans la première ligne de la table pour déterminer les noms de champ et qu’elle doit examiner la totalité du fichier pour déterminer les données de types utilisés :  
  
```  
ColNameHeader=True  
MaxScanRows=0  
```  
  
 L’entrée suivante désigne les champs dans une table en utilisant le numéro de colonne (**Col**_n_) option, qui est facultatif pour les fichiers délimités par un caractère et requis pour les fichiers de longueur fixe. L’exemple montre les entrées Schema.ini pour deux champs, un champ de texte CustomerNumber 10 caractères et un champ de texte CustomerName 30 caractères :  
  
```  
Col1=CustomerNumber Text Width 10  
Col2=CustomerName Text Width 30  
```  
  
 La syntaxe de **Col**_n_ est :  
  
```  
  
n=ColumnNametype [#]  
```  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant décrit chaque partie de la **Col**_n_ entrée.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*ColumnName*|Le nom de texte de la colonne. Si le nom de colonne contienne des espaces incorporés, vous devez le placer entre guillemets doubles.|  
|*type*|Types de données sont les suivantes :<br /><br /> **Types de données Microsoft Jet**<br /><br /> bit<br /><br /> Byte<br /><br /> Short<br /><br /> Long<br /><br /> Currency<br /><br /> Unique<br /><br /> Double<br /><br /> DateTime<br /><br /> Text<br /><br /> Mémo<br /><br /> **Types de données ODBC** Char (sous forme de texte)<br /><br /> Float (comme Double)<br /><br /> Integer (comme court)<br /><br /> LongChar (comme Mémo)<br /><br /> Date *format de date*|  
|**Width**|La valeur de chaîne littérale `Width`. Indique que le nombre suivant désigne la largeur de la colonne (facultatif pour les fichiers délimités par des caractères ; obligatoire pour les fichiers de longueur fixe).|  
|*#*|La valeur entière qui désigne la largeur de la colonne (obligatoire si **largeur** est spécifié).|  
  
## <a name="selecting-a-character-set"></a>Sélection d’un jeu de caractères  
 Vous pouvez sélectionner à partir de deux jeux de caractères : ANSI et OEM. Le **CharacterSet** paramètre dans Schema.ini remplace le paramètre dans le Registre Windows, fichier par fichier. L’exemple suivant illustre l’entrée de Schema.ini qui définit le jeu de caractères à ANSI :  
  
```  
CharacterSet=ANSI  
```  
  
## <a name="specifying-data-type-formats-and-conversions"></a>Spécification des Formats de Type de données et les Conversions  
 Le fichier Schema.ini contient plusieurs options que vous pouvez utiliser pour spécifier comment les données sont converties ou affichées. Le tableau suivant répertorie chacune de ces options.  
  
|Option|Description|  
|------------|-----------------|  
|**DateTimeFormat**|Peut être définie à une chaîne de format qui indique les dates et heures. Vous devez spécifier cette entrée si tous les champs de date/heure de l’importation/exportation sont traités avec le même format. Tous les formats de Microsoft Jet, à l’exception du matin. et heures. sont pris en charge. S’il n’existe aucune chaîne de format, les options de date courte le panneau de configuration Windows image et l’heure sont utilisées.|  
|**DecimalSymbol**|Peut être définie sur n’importe quel caractère unique qui est utilisé pour séparer l’entier à partir de la partie fractionnaire d’un nombre.|  
|**NumberDigits**|Indique le nombre de chiffres décimaux dans la partie fractionnaire d’un nombre.|  
|**NumberLeadingZeros**|Spécifie si une valeur décimale inférieure à 1 et plus de -1 doit contenir des zéros non significatifs ; Cette valeur peut être soit False (sans zéros) ou True.|  
|**CurrencySymbol**|Indique le symbole monétaire qui peut être utilisé pour les valeurs monétaires dans le fichier texte. Le signe dollar ($) et exemples Dm.|  
|**CurrencyPosFormat**|Peut être définie à une des valeurs suivantes :<br /><br /> -Préfixe de symbole de devise sans séparation ($1)<br />-Suffixe de symbole de devise sans séparation (1$)<br />-Préfixe de symbole de devise avec la séparation d’un caractère ($ 1)<br />-Suffixe de symbole de devise avec la séparation d’un caractère (1 $)|  
|**CurrencyDigits**|Spécifie le nombre de chiffres utilisés pour la partie fractionnaire d’un montant monétaire.|  
|**CurrencyNegFormat**|Peut avoir l'une des valeurs suivantes :<br /><br /> -   ($1)<br />-   -$1<br />-   $-1<br />-   $1-<br />-   (1$)<br />-   -1$<br />-   1-$<br />-   1$-<br />-   -1 $<br />-   -$ 1<br />-   1 $-<br />-   $ 1-<br />-   $ -1<br />-   1- $<br />-   ($ 1)<br />-   (1 $)<br /><br /> Cet exemple montre le signe dollar, mais vous devez le remplacer avec le bon **CurrencySymbol** valeur dans le programme.|  
|**CurrencyThousandSymbol**|Indique le symbole de caractère unique qui peut être utilisé pour séparer les valeurs de devise dans le fichier texte par des milliers.|  
|**CurrencyDecimalSymbol**|Peut être définie sur n’importe quel caractère unique qui est utilisé pour séparer la totalité de la partie fractionnaire d’un montant monétaire.|  
  
> [!NOTE]  
>  Si vous omettez une entrée, la valeur par défaut dans le panneau de configuration de Windows est utilisée.
