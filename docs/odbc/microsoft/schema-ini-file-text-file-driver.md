---
title: Fichier Schema.ini (Text File Driver) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305510"
---
# <a name="schemaini-file-text-file-driver"></a>Fichier Schema.ini (pilote du fichier texte)
Lorsque le pilote de texte est utilisé, le format du fichier texte est déterminé à l’aide d’un fichier d’information schématique. Le fichier d’information schématique est toujours nommé Schema.ini et toujours conservé dans le même répertoire que la source de données de texte. Le fichier d’information sur les schémas fournit à l’IISAM des informations sur le format général du fichier, le nom de colonne et les informations de type de données, ainsi que plusieurs autres caractéristiques de données. Un fichier Schema.ini est toujours nécessaire pour accéder aux données à durée fixe. Vous devez utiliser un fichier Schema.ini lorsque votre table texte contient des données DateTime, Monnaie ou Décimale, ou à tout moment où vous voulez plus de contrôle sur le traitement des données dans le tableau.  
  
> [!NOTE]  
>  Le texte ISAM obtiendra les valeurs initiales du registre, et non de Schema.ini. Le même format de fichier par défaut s’applique à toutes les nouvelles tables de données textuelles. Tous les fichiers créés par la déclaration CREATE TABLE héritent de ces mêmes valeurs de format \<par défaut, qui sont définies en sélectionnant les valeurs de format de fichier dans la boîte de dialogue Define Text **Format** avec> par défaut choisies dans la liste des **tables.** Si les valeurs du registre diffèrent des valeurs de Schema.ini, les valeurs du registre seront remplacées par les valeurs de Schema.ini.  
  
## <a name="understanding-schemaini-files"></a>Comprendre schema.ini Fichiers  
 Les fichiers Schema.ini fournissent des informations sur les dossiers dans un fichier texte. Chaque entrée Schema.ini précise l’une des cinq caractéristiques de la table :  
  
-   Le nom du fichier texte  
  
-   Le format du fichier  
  
-   Les noms de champ, les largeurs et les types  
  
-   L’ensemble de caractères  
  
-   Conversions spéciales de type de données  
  
 Les sections suivantes traitent de ces caractéristiques.  
  
## <a name="specifying-the-file-name"></a>Spécifier le nom du fichier  
 La première entrée dans Schema.ini est toujours le nom du fichier source de texte enfermé dans les parenthèses carrées. L’exemple suivant illustre l’entrée pour le fichier Sample.txt:  
  
```  
[Sample.txt]  
```  
  
## <a name="specifying-the-file-format"></a>Spécifier le format de fichier  
 **L’option Format** dans Schema.ini précise le format du fichier texte. Le Texte IISAM peut lire le format automatiquement à partir de la plupart des fichiers délimités par les personnages. Vous pouvez utiliser n’importe quel personnage unique comme délimitant dans le fichier, sauf la double marque de citation ("). Le paramètre **Format** dans Schema.ini remplace le paramètre dans le Registre Windows, fichier par fichier. Le tableau suivant répertorie les valeurs valides pour l’option **Format.**  
  
|Spécificateur de format|Format de table|Déclaration de format Schema.ini|  
|----------------------|------------------|---------------------------------|  
|**Onglet Délimité**|Les champs dans le fichier sont délimités par des onglets.|Format-TabDelimited|  
|**CSV délimité**|Les champs du fichier sont délimités par des virgules (valeurs séparées par virgule).|Format-CSVDelimited|  
|**Délimité personnalisé**|Les champs dans le fichier sont délimités par n’importe quel personnage que vous choisissez d’entrer dans la boîte de dialogue. Tous sauf les doubles guillemets (") sont autorisés, y compris vide.|Format-Delimited *(caractère personnalisé*)<br /><br /> -ou-<br /><br /> Sans délimiter spécifié :<br /><br /> Format-Delimited( )|  
|**Longueur fixe**|Les champs dans le fichier sont d’une longueur fixe.|Format-FixedLength|  
  
## <a name="specifying-the-fields"></a>Spécifier les champs  
 Vous pouvez spécifier les noms de champ dans un fichier texte délimité par les personnages de deux façons :  
  
-   Inclure les noms de terrain dans la première rangée de la table et mettre **ColNameHeader** à **Vrai.**  
  
-   Spécifiez chaque colonne par numéro et désignez le nom de colonne et le type de données.  
  
 Vous devez spécifier chaque colonne par numéro et désigner le nom de colonne, le type de données et la largeur des fichiers à durée fixe.  
  
> [!NOTE]  
>  Le paramètre **ColNameHeader** dans Schema.ini remplace le paramètre **FirstRowHasNames** dans le Registre Windows, fichier par fichier.  
  
 Les types de données des champs peuvent également être déterminés. Utilisez l’option **MaxScanRows** pour indiquer combien de lignes doivent être numérisées lors de la détermination des types de colonnes. Si vous **définissez MaxScanRows** à 0, l’ensemble du fichier est numérisé. Le paramètre **MaxScanRows** dans Schema.ini remplace le paramètre du Registre Windows, fichier par fichier.  
  
 L’entrée suivante indique que Microsoft Jet devrait utiliser les données dans la première rangée de la table pour déterminer les noms de terrain et devrait examiner l’ensemble du fichier pour déterminer les types de données utilisés:  
  
```  
ColNameHeader=True  
MaxScanRows=0  
```  
  
 L’entrée suivante désigne les champs dans un tableau en utilisant l’option numéro de colonne (**Col**_n_), qui est facultative pour les fichiers délimités par les caractères et requise pour les fichiers à durée fixe. L’exemple montre les entrées Schema.ini pour deux domaines, un champ de texte CustomerNumber de 10 caractères et un champ de texte CustomerName de 30 caractères :  
  
```  
Col1=CustomerNumber Text Width 10  
Col2=CustomerName Text Width 30  
```  
  
 La syntaxe de **Col**_n_ est:  
  
```  
  
n=ColumnNametype [#]  
```  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant décrit chaque partie de l’entrée **du Col**_n._  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*ColumnName*|Le nom de texte de la colonne. Si le nom de la colonne contient des espaces intégrés, vous devez l’enfermer dans des guillemets doubles.|  
|*type*|Les types de données sont les suivants :<br /><br /> **Types de données Microsoft Jet**<br /><br /> bit<br /><br /> Byte<br /><br /> Court<br /><br /> Long<br /><br /> Devise<br /><br /> Unique<br /><br /> Double<br /><br /> DateTime<br /><br /> Texte<br /><br /> Mémo<br /><br /> **Types de données ODBC** Char (même que le texte)<br /><br /> Flotteur (même que Double)<br /><br /> Integer (même que Short)<br /><br /> LongChar (même que Memo)<br /><br /> *Format de date de date*|  
|**Width**|La valeur `Width`de la chaîne littérale . Indique que le numéro suivant désigne la largeur de la colonne (facultatif pour les fichiers délimités par les caractères; requis pour les fichiers à durée fixe).|  
|*#*|La valeur de l’intégrant qui désigne la largeur de la colonne (nécessaire si **la largeur** est spécifiée).|  
  
## <a name="selecting-a-character-set"></a>Sélection d’un ensemble de caractères  
 Vous pouvez sélectionner parmi deux ensembles de personnages : ANSI et OEM. Le paramètre **CharacterSet** dans Schema.ini remplace le paramètre dans le Registre Windows, fichier par fichier. L’exemple suivant montre l’entrée Schema.ini qui définit le personnage mis à ANSI:  
  
```  
CharacterSet=ANSI  
```  
  
## <a name="specifying-data-type-formats-and-conversions"></a>Spécifier les formats et les conversions de type de données  
 Le fichier Schema.ini contient plusieurs options que vous pouvez utiliser pour spécifier la façon dont les données sont converties ou affichées. Le tableau suivant répertorie chacune de ces options.  
  
|Option|Description|  
|------------|-----------------|  
|**DateTimeFormat**|Peut être réglé sur une chaîne de format qui indique les dates et les heures. Vous devez spécifier cette entrée si tous les champs de date/heure de l’importation/exportation sont traités avec le même format. Tous les formats Microsoft Jet sauf A.M. et P.M sont pris en charge. S’il n’y a pas de chaîne de format, l’image de date courte et les options d’heure du panneau de contrôle Windows sont utilisées.|  
|**DécimamalSymbol**|Peut être réglé à n’importe quel personnage unique qui est utilisé pour séparer l’intégrant de la partie fractionnaire d’un nombre.|  
|**NombreDigits**|Indique le nombre de chiffres décimaux dans la partie fractionnaire d’un nombre.|  
|**NombreLeadingZeros**|Précise si une valeur décimale inférieure à 1 et supérieure à -1 devrait contenir des zéros de premier plan; cette valeur peut être soit fausse (pas de zéros de premier plan) ou Vrai.|  
|**CurrencySymbol**|Indique le symbole de change qui peut être utilisé pour les valeurs de change dans le fichier texte. Par exemple, le signe en dollars ($) et le Dm.|  
|**MonnaiePosFormat**|Peut être réglé à l’une des valeurs suivantes :<br /><br /> - Préfixe de symbole de devise sans séparation ($1)<br />- Suffixe de symbole de devise sans séparation (1$)<br />- Préfixe de symbole de devise avec une séparation de caractère ($ 1)<br />- Suffixe de symbole de devise avec une séparation de caractère (1 $)|  
|**CurrencyDigits**|Spécifie le nombre de chiffres utilisés pour la partie fractionnaire d’un montant de devise.|  
|**MonnaieNegFormat**|Il peut s'agir de l'une des valeurs suivantes :<br /><br /> - (1 $)<br />- -$1<br />- $-1<br />- 1 $<br />- (1$)<br />- -1$<br />- 1-$<br />- 1$-<br />- -1 $<br />- -$ 1<br />- 1 $-<br />- $ 1-<br />- $ -1<br />- 1- $<br />- (1 $ )<br />- (1 $)<br /><br /> Cet exemple montre le signe du dollar, mais vous devez le remplacer par la valeur **appropriée de CurrencySymbol** dans le programme réel.|  
|**MonnaieThousandSymbol**|Indique le symbole à caractère unique qui peut être utilisé pour séparer les valeurs de change dans le fichier texte par milliers.|  
|**MonnaieDecimalSymbol**|Peut être réglé à n’importe quel personnage unique qui est utilisé pour séparer l’ensemble de la partie fractionnaire d’un montant de devise.|  
  
> [!NOTE]  
>  Si vous ometez une entrée, la valeur par défaut du panneau de contrôle Windows est utilisée.
