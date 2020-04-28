---
title: Fichier Schema. ini (pilote de fichier texte) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 365351724f27205e7d460c757f1268d042cefc76
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305510"
---
# <a name="schemaini-file-text-file-driver"></a>Fichier Schema.ini (pilote du fichier texte)
Lorsque le pilote de texte est utilisé, le format du fichier texte est déterminé à l’aide d’un fichier d’informations de schéma. Le fichier d’informations de schéma est toujours nommé Schema. ini et toujours conservé dans le même répertoire que la source de données texte. Le fichier d’informations de schéma fournit à l’IISAM des informations sur le format général du fichier, le nom de colonne et les informations sur le type de données, ainsi que plusieurs autres caractéristiques de données. Un fichier Schema. ini est toujours requis pour l’accès aux données de longueur fixe. Vous devez utiliser un fichier Schema. ini lorsque votre table de texte contient des données de type DateTime, Currency ou Decimal, ou à chaque fois que vous souhaitez plus de contrôle sur la gestion des données dans la table.  
  
> [!NOTE]  
>  L’ISAM de texte obtiendra les valeurs initiales du Registre, et non de Schema. ini. Le même format de fichier par défaut s’applique à toutes les nouvelles tables de données de texte. Tous les fichiers qui ont été créés par l’instruction CREATE TABLE héritent des mêmes valeurs de format par défaut, qui sont définies en sélectionnant des valeurs de format de \<fichier dans la boîte de dialogue définir le format de **texte** avec les> par défaut choisies dans la liste **tables** . Si les valeurs du Registre diffèrent des valeurs de Schema. ini, les valeurs du Registre seront remplacées par les valeurs de Schema. ini.  
  
## <a name="understanding-schemaini-files"></a>Fonctionnement des fichiers Schema. ini  
 Les fichiers Schema. ini fournissent des informations de schéma sur les enregistrements d’un fichier texte. Chaque entrée Schema. ini spécifie l’une des cinq caractéristiques de la table :  
  
-   Nom du fichier texte  
  
-   Le format de fichier  
  
-   Noms de champs, largeurs et types  
  
-   Jeu de caractères  
  
-   Conversions de types de données spéciaux  
  
 Les sections suivantes décrivent ces caractéristiques.  
  
## <a name="specifying-the-file-name"></a>Spécification du nom de fichier  
 La première entrée dans Schema. ini est toujours le nom du fichier de source de texte placé entre crochets. L’exemple suivant illustre l’entrée du fichier Sample. txt :  
  
```  
[Sample.txt]  
```  
  
## <a name="specifying-the-file-format"></a>Spécification du format de fichier  
 L’option **format** dans Schema. ini spécifie le format du fichier texte. L’IISAM de texte peut lire le format automatiquement à partir de la plupart des fichiers délimités par des caractères. Vous pouvez utiliser n’importe quel caractère unique comme délimiteur dans le fichier, à l’exception du guillemet double ("). Le paramètre **format** dans Schema. ini remplace le paramètre dans le Registre Windows, file by file. Le tableau suivant répertorie les valeurs valides pour l’option **format** .  
  
|Spécificateur de format|Format de table|Schema. ini (instruction de format)|  
|----------------------|------------------|---------------------------------|  
|**Délimité par des tabulations**|Les champs du fichier sont délimités par des tabulations.|Format = TabDelimited|  
|**Délimité CSV**|Les champs du fichier sont délimités par des virgules (valeurs séparées par des virgules).|Format = CSVDelimited|  
|**Délimité personnalisé**|Les champs du fichier sont délimités par n’importe quel caractère que vous choisissez d’entrer dans la boîte de dialogue. Tous les guillemets (") sont autorisés, y compris les guillemets doubles (").|Format = délimité (*caractère personnalisé*)<br /><br /> -ou-<br /><br /> Sans délimiteur spécifié :<br /><br /> Format = délimité ()|  
|**Longueur fixe**|Les champs du fichier ont une longueur fixe.|Format = multiple|  
  
## <a name="specifying-the-fields"></a>Spécification des champs  
 Vous pouvez spécifier des noms de champ dans un fichier texte délimité par des caractères de deux manières :  
  
-   Incluez les noms de champs dans la première ligne de la table et affectez à **ColNameHeader** la **valeur true.**  
  
-   Spécifiez chaque colonne par nombre et spécifiez le nom de colonne et le type de données.  
  
 Vous devez spécifier chaque colonne par nombre et désigner le nom de colonne, le type de données et la largeur des fichiers de longueur fixe.  
  
> [!NOTE]  
>  Le paramètre **ColNameHeader** dans Schema. ini remplace le paramètre **FirstRowHasNames** dans le Registre Windows, file by file.  
  
 Les types de données des champs peuvent également être déterminés. Utilisez l’option **MaxScanRows** pour indiquer le nombre de lignes qui doivent être analysées lors de la détermination des types de colonne. Si vous affectez à **MaxScanRows** la valeur 0, la totalité du fichier est analysée. Le paramètre **MaxScanRows** dans Schema. ini remplace le paramètre dans le Registre Windows, file by file.  
  
 L’entrée suivante indique que Microsoft Jet doit utiliser les données de la première ligne du tableau pour déterminer les noms des champs et doit examiner l’ensemble du fichier pour déterminer les types de données utilisés :  
  
```  
ColNameHeader=True  
MaxScanRows=0  
```  
  
 L’entrée suivante désigne les champs d’une table à l’aide de l’option column Number (**col**_n_), qui est facultative pour les fichiers délimités par des caractères et requis pour les fichiers de longueur fixe. L’exemple montre les entrées de Schema. ini pour deux champs, un champ de texte CustomerNumber de 10 caractères et un champ de texte CustomerName de 30 caractères :  
  
```  
Col1=CustomerNumber Text Width 10  
Col2=CustomerName Text Width 30  
```  
  
 La syntaxe de **col**_n_ est la suivante :  
  
```  
  
n=ColumnNametype [#]  
```  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant décrit chaque partie de l’entrée **col**_n_ .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*ColumnName*|Nom de texte de la colonne. Si le nom de colonne contient des espaces incorporés, vous devez le placer entre guillemets doubles.|  
|*type*|Les types de données sont les suivants :<br /><br /> **Types de données Microsoft Jet**<br /><br /> bit<br /><br /> Byte<br /><br /> Court<br /><br /> Long<br /><br /> Devise<br /><br /> Unique<br /><br /> Double<br /><br /> DateTime<br /><br /> Texte<br /><br /> Mémo<br /><br /> **Types de données ODBC** Char (identique au texte)<br /><br /> Float (identique à double)<br /><br /> Entier (identique à Short)<br /><br /> LongChar (identique à MEMO)<br /><br /> Date *format date*|  
|**Width**|Valeur `Width`de chaîne littérale. Indique que le nombre suivant désigne la largeur de la colonne (facultatif pour les fichiers délimités par des caractères ; obligatoire pour les fichiers de longueur fixe).|  
|*#*|Valeur entière qui désigne la largeur de la colonne (obligatoire si la **largeur** est spécifiée).|  
  
## <a name="selecting-a-character-set"></a>Sélection d’un jeu de caractères  
 Vous pouvez sélectionner deux jeux de caractères : ANSI et OEM. Le paramètre **CharacterSet** dans Schema. ini remplace le paramètre dans le Registre Windows, file by file. L’exemple suivant illustre l’entrée Schema. ini qui définit le jeu de caractères sur ANSI :  
  
```  
CharacterSet=ANSI  
```  
  
## <a name="specifying-data-type-formats-and-conversions"></a>Spécification de formats et de conversions de types de données  
 Le fichier Schema. ini contient plusieurs options que vous pouvez utiliser pour spécifier la façon dont les données sont converties ou affichées. Le tableau suivant répertorie chacune de ces options.  
  
|Option|Description|  
|------------|-----------------|  
|**DateTimeFormat**|Peut être défini sur une chaîne de format qui indique les dates et les heures. Vous devez spécifier cette entrée si tous les champs de date/heure de l’importation/exportation sont gérés avec le même format. Tous les formats Microsoft Jet sauf A.M. et P.M sont pris en charge. S’il n’y a pas de chaîne de format, les options d’image et d’heure de la date abrégée du panneau de configuration Windows sont utilisées.|  
|**DecimalSymbol**|Peut être défini sur n’importe quel caractère unique utilisé pour séparer l’entier de la partie fractionnaire d’un nombre.|  
|**NumberDigits**|Indique le nombre de chiffres décimaux dans la partie fractionnaire d’un nombre.|  
|**NumberLeadingZeros**|Spécifie si une valeur décimale inférieure à 1 et supérieure à-1 doivent contenir des zéros non significatifs. Cette valeur peut être false (sans zéro non significatif) ou true.|  
|**CurrencySymbol**|Indique le symbole monétaire qui peut être utilisé pour les valeurs monétaires dans le fichier texte. Les exemples incluent le signe dollar ($) et le DM (DM).|  
|**CurrencyPosFormat**|Peut être défini sur l’une des valeurs suivantes :<br /><br /> -Préfixe de symbole monétaire sans séparation ($1)<br />-Suffixe de symbole monétaire sans séparation ($1)<br />-Préfixe de symbole monétaire avec une séparation de caractères ($1)<br />-Suffixe de symbole monétaire avec une séparation de caractères ($1)|  
|**CurrencyDigits**|Spécifie le nombre de chiffres utilisés pour la partie fractionnaire d’un montant en devise.|  
|**CurrencyNegFormat**|Peut avoir l’une des valeurs suivantes :<br /><br /> -($1)<br />--$1<br />-$-1<br />-$1-<br />-($1)<br />--$1<br />-1-$<br />-$1-<br />--$1<br />--$1<br />-$1-<br />-$1-<br />-$-1<br />-1-$<br />-($1)<br />-($1)<br /><br /> Cet exemple montre le signe dollar, mais vous devez le remplacer par la valeur **CurrencySymbol** appropriée dans le programme réel.|  
|**CurrencyThousandSymbol**|Indique le symbole à un seul caractère qui peut être utilisé pour séparer les valeurs monétaires dans le fichier texte par des milliers.|  
|**CurrencyDecimalSymbol**|Peut être défini sur n’importe quel caractère unique utilisé pour séparer l’ensemble de la partie fractionnaire d’un montant monétaire.|  
  
> [!NOTE]  
>  Si vous omettez une entrée, la valeur par défaut dans le panneau de configuration Windows est utilisée.
