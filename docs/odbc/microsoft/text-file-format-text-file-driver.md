---
title: Format de fichier texte (Pilote de fichiers texte) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- delimited text lines
- fixed-width text files
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: f53cd4b5-0721-4562-a90f-4c55e6030cb9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5801433e0180bb07cb2d09a59db2bb74be012cdf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303090"
---
# <a name="text-file-format-text-file-driver"></a>Format du fichier texte (pilote de fichier texte)
Le pilote de texte ODBC prend en charge les fichiers texte délimités et à largeur fixe. Un fichier texte se compose d’une ligne d’en-tête facultative et de lignes de texte nulles ou plus.  
  
 Bien que la ligne d’en-tête utilise le même format que les autres lignes du fichier texte, le pilote de texte ODBC interprète les entrées de la ligne d’en-tête comme des noms de colonne, et non des données.  
  
 Une ligne de texte délimitée contient une ou plusieurs valeurs de données séparées par des délimitants : virgules, onglets ou délimitants personnalisés. Le même délimitant doit être utilisé dans tout le fichier. Les valeurs de données nulles sont notées par deux délimitants d’affilée sans données entre elles. Les chaînes de caractères d’une ligne de texte délimitée peuvent être incluses dans des doubles guillemets (« »). Aucun blanc ne peut se produire avant ou après des valeurs délimitées.  
  
 La largeur de chaque entrée de données dans une ligne de texte à largeur fixe est spécifiée dans un schéma. Les valeurs de données nulles sont notées par des blancs.  
  
 Les tables sont limitées à un maximum de 255 champs. Les noms de terrain sont limités à 64 caractères, et les largeurs de champ sont limitées à 32 766 caractères. Les dossiers sont limités à 65 000 octets.  
  
 Un fichier texte ne peut être ouvert que pour un seul utilisateur. Plusieurs utilisateurs ne sont pas pris en charge.  
  
 La grammaire suivante, écrite pour les programmeurs, définit le format d’un fichier texte qui peut être lu par le facteur texte ODBC :  
  
|Format|Représentation|  
|------------|--------------------|  
|Non-italique|Caractères qui doivent être entrés comme indiqué|  
|*Italique*|Arguments définis ailleurs dans la grammaire|  
|parenthèses ([])|Éléments facultatifs|  
|accolades{}( )|Une liste de choix mutuellement exclusifs|  
|barres verticales (&#124;)|Séparer les choix mutuellement exclusifs|  
|points de suspension (...)|Articles qui peuvent être répétés une ou plusieurs fois|  
  
 Le format d’un fichier texte est :  
  
```  
text-file ::=  
   [delimited-header-line] [delimited-text-line]... end-of-file |  
   [fixed-width-header-line] [fixed-width-text-line]... end-of-file  
delimited-header-line ::= delimited-text-line  
delimited-text-line ::=  
   blank-line |  
   delimited-data [delimiter delimited-data]... end-of-line  
fixed-width-header-line ::= fixed-width-text-line  
fixed-width-text-line ::=  
   blank-line |  
   fixed-width-data [fixed-width-data]... end-of-line  
end-of-file ::= <EOF>  
blank-line ::= end-of-line  
delimited-data ::= delimited-string | number | date | delimited-null  
fixed-width-data ::= fixed-width-string | number | date | fixed-width-null  
```  
  
> [!NOTE]  
>  La largeur de chaque colonne dans un fichier texte à largeur fixe est spécifiée dans le fichier Schema.ini.  
  
```  
  
      end-of-line ::= <CR> | <LF> | <CR><LF>  
delimited-string ::= unquoted-string | quoted-stringunquoted-string ::= [character | digit] [character | digit | quote-character]...  
quoted-string ::=  
   quote-character  
   [character | digit | delimiter | end-of-line | embedded-quoted-string]...  
   quote-characterembedded-quoted-string ::=   quote-characterquote-character  
   [character | digit | delimiter | end-of-line]  
   quote-characterquote-characterfixed-width-string ::= [character | digit | delimiter | quote-character] ...  
character ::= any character except:  
   delimiterdigitend-of-fileend-of-linequote-characterdigit ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9  
delimiter ::= , | <TAB> |   
custom-delimitercustom-delimiter ::= any character except:  
   end-of-fileend-of-linequote-character  
```  
  
> [!NOTE]  
>  Le délimitant dans un fichier texte délimité sur mesure est spécifié dans le fichier Schema.ini.  
  
```  
quote-character ::= "  
number ::= exact-number | approximate-number  
exact-number ::= [+ | -] {unsigned-integer[.unsigned-integer] |  
   unsigned-integer. |  
   .unsigned-integer}  
approximate-number ::= exact-number{e | E}[+ | -]unsigned-integer  
unsigned-integer ::= {digit}...  
date ::=  
   mm date-separator dd date-separator yy |  
   mmm date-separator dd date-separator yy |  
   dd date-separator mmm date-separator yy |  
   yyyy date-separator mm date-separator dd |  
   yyyy date-separator mmm date-separator dd  
mm ::= digit [digit]  
dd ::= digit [digit]  
yy ::= digit digit  
yyyy ::= digit digit digit digit  
mmm ::= Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec  
date-separator ::= - | / | .  
delimited-null ::=  
```  
  
> [!NOTE]  
>  Pour les fichiers délimités, un NULL n’est représenté par aucune donnée entre deux délimitants.  
  
```  
fixed-width-null ::= <SPACE>...  
```  
  
> [!NOTE]  
>  Pour les fichiers à largeur fixe, un NULL est représenté par des espaces.
