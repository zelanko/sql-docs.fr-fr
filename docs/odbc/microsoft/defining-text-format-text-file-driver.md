---
title: Définir le format de texte (Text File Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: 3af46dad-52cc-4d5c-a27e-6315d65a74e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 29dc46525f3c81e5abffe5076988716a01df06df
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307660"
---
# <a name="defining-text-format-text-file-driver"></a>Définition du format du texte (pilote de fichier texte)
Lorsque le pilote de texte est utilisé, vous pouvez utiliser la boîte de dialogue **Définir le format de texte** pour définir le format pour les colonnes dans un fichier sélectionné. Cette boîte de dialogue vous permet de spécifier le schéma de chaque table de données. Ces informations sont écrites à un fichier Schema.ini dans le répertoire de source de données. Un fichier Schema.ini séparé est créé pour chaque répertoire source de données de texte.  
  
> [!NOTE]  
>  Le même format de fichier par défaut s’applique à toutes les nouvelles tables de données textuelles. Tous les fichiers créés par la déclaration CREATE TABLE héritent de ces mêmes valeurs de \<format par défaut, qui sont définies en sélectionnant les valeurs de format de fichier dans la boîte de dialogue Define Text **Format** avec> par défaut choisies dans la liste des **tables.** Le pilote de texte ne modifie pas le format d’un fichier texte existant pour correspondre au format défini dans cette boîte de dialogue, mais renvoie une erreur lorsqu’il utilise le format, par exemple lorsqu’il tente de récupérer des données du fichier texte.  
  
 Les options suivantes sont disponibles dans la boîte de dialogue **Define Text Format** :  
  
|Option|Information|  
|------------|-----------------|  
|**Ajouter**|Ajoute une colonne en utilisant les valeurs dans **Data Type**, **Nom**, et **Largeur** de la boîte de dialogue, et le cas échéant, la valeur de séparation de date de Schema.ini.|  
|**Personnages**|**ANSI** ou **OEM**. OEM spécifie un ensemble de caractères non-ANSI. Cela est par défaut pour OEM si le format de l’élément sélectionné dans la liste **des tables** n’a pas été précédemment défini par cette boîte de dialogue.|  
|**En-tête de nom de colonne**|Indique si les colonnes de la première rangée de la table sélectionnée doivent être utilisées comme noms de colonne. SOIT **VRAI** ou **FALSE**. Par défaut à FALSE si le format de l’élément sélectionné dans la liste **des tables n’a** pas été précédemment défini par cette boîte de dialogue.|  
|**Colonnes**|Répertorie les noms de colonnes pour chaque colonne dans le tableau sélectionné. L’ordre des colonnes reflète l’ordre des colonnes dans la table. Cette liste est activée si un fichier a été sélectionné dans la liste **des tables.**|  
|**Type de données**|Peut être BIT, BYTE, CHAR, CURRENCY, DATE, FLOAT, INTEGER, LONGCHAR, SHORT, ou SINGLE. Les types de données de date peuvent être dans les formats suivants : " dd-mmm-yy ", " mm-dd-yy ", " mmm-dd-yy ", " yyyy-mm-dd ", ou " yyyyy-mmm-dd ". "mm" dénote les chiffres pendant des mois; "mmm" dénote des lettres pendant des mois.|  
|**Délimiteur**|Spécifie le caractère de délimitant personnalisé à utiliser pour séparer les colonnes. Activé lorsque le format **Custom Delimited** est sélectionné. Le délimital ne peut être qu’un seul personnage de longueur, et les doubles guillemets () ne peuvent pas être utilisés comme caractère délimitant. (Le délimital ne peut pas être spécifié dans le format hexadecimal ou décimal.)|  
|**Format**|Longueur délimitée ou fixe. S’il est délimité, indique le type de délimital utilisé : virgule (CSV), onglet ou caractère spécial (personnalisé). Cela est par défaut pour **CSV Délimité** si le format de l’élément sélectionné dans la liste **des tables** n’a pas été précédemment défini par cette boîte de dialogue.<br /><br /> Si **le format** est de longueur fixe et que **l’en-tête de nom de colonne** est VRAI, la première ligne doit être délimitée par virgule.|  
|**Deviner**|Génère automatiquement le type de données, le nom et les valeurs de largeur de la colonne pour les colonnes dans le tableau sélectionné en scannant le contenu de la table en fonction de la sélection de la boîte **Format.** Activé lorsque le format de table est délimité. Toutes les colonnes précédemment définies dans la liste **des colonnes** sont effacées et remplacées par de nouvelles entrées. Si **l’en-tête de nom de colonne** n’est pas sélectionné, les noms de colonnes sont générés automatiquement sous le nom de « F1 », « F2 », et ainsi de suite. Aucune valeur par défaut n’est indiquée dans la boîte **de type de données.**<br /><br /> Cette fonctionnalité ne fonctionne que sur des colonnes de moins de 64 513 octets.|  
|**Modify**|Modifie la colonne sélectionnée en utilisant les valeurs dans **Data Type**, **Nom**, et **Largeur**.|  
|**Nom**|Affiche le nom de la colonne sélectionnée. Peut être utilisé pour spécifier un nouveau nom de colonne pour une colonne existante ou une nouvelle colonne.<br /><br /> Si **l’en-tête de nom de colonne** est VRAI, le nom de colonne affiché est ignoré.|  
|**Supprimer**|Supprime la colonne sélectionnée.|  
|**Lignes à scanner**|Le nombre de lignes que configurer ou le pilote analyse lors de la configuration des colonnes et des types de données de colonnes en fonction des données existantes.<br /><br /> Vous pouvez entrer un numéro de 1 à 32767 pour le nombre de lignes à numériser. Ce défaut est de 25 si le format de l’élément sélectionné dans la liste **des tables** n’a pas été précédemment défini par cette boîte de dialogue. (Un numéro en dehors de la limite retournera une erreur.)|  
|**Tables**|Contient une liste de tous les fichiers dans l’annuaire sélectionné dans la boîte de dialogue **Text Setup** qui correspondent à la liste des extensions spécifiées.<br /><br /> Lorsque \<le défaut> est sélectionné, et l’une des suivantes est vraie, les valeurs des attributs de table dans le groupe **Tables** sont écrites à Schema.ini (aucune autre entrée dans Schema.ini sont touchés):<br /><br /> - Il n’y a pas de Schema.ini dans l’annuaire spécifié.<br />- Le fichier Schema.ini existe, mais il n’y a pas de section dans Schema.ini pour l’un des fichiers texte (avec l’extension spécifiée) dans l’annuaire.<br />- La section d’un fichier texte existe à Schema.ini, mais le corps est vide.<br /><br /> Lorsque \<> par défaut est sélectionnée, le groupe **Colonnes** est désactivé.|  
|**Width**|La largeur de la colonne peut être modifiée pour les colonnes CHAR ou LONGCHAR. La largeur par défaut à 1 si le format de l’élément sélectionné dans la liste **des tables** n’a pas été précédemment défini par cette boîte de dialogue.<br /><br /> Pour d’autres types de données, le contrôle de largeur est désactivé et aucune valeur n’est affichée.|
