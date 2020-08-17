---
description: Définition du format du texte (pilote de fichier texte)
title: Définition du format texte (pilote de fichier texte) | Microsoft Docs
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
ms.openlocfilehash: fe992d4ea7cf81387bc56ef9c384404b015b52a9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340945"
---
# <a name="defining-text-format-text-file-driver"></a>Définition du format du texte (pilote de fichier texte)
Lorsque le pilote de texte est utilisé, vous pouvez utiliser la boîte de dialogue **définir le format du texte** pour définir le format des colonnes dans un fichier sélectionné. Cette boîte de dialogue vous permet de spécifier le schéma de chaque table de données. Ces informations sont écrites dans un fichier de Schema.ini dans le répertoire de la source de données. Un fichier de Schema.ini distinct est créé pour chaque répertoire de source de données de texte.  
  
> [!NOTE]  
>  Le même format de fichier par défaut s’applique à toutes les nouvelles tables de données de texte. Tous les fichiers créés par l’instruction CREATE TABLE héritent des mêmes valeurs de format par défaut, qui sont définies en sélectionnant des valeurs de format de fichier dans la boîte de dialogue **définir le format de texte** , avec l’option \<default> choisie dans la liste **tables** . Le pilote de texte ne change pas le format d’un fichier texte existant pour qu’il corresponde au format défini dans cette boîte de dialogue, mais retourne une erreur lorsqu’il utilise le format, par exemple lorsqu’il tente d’extraire des données du fichier texte.  
  
 Les options suivantes sont disponibles dans la boîte de dialogue **définir le format du texte** :  
  
|Option|Information|  
|------------|-----------------|  
|**Ajouter**|Ajoute une colonne à l’aide des valeurs dans le **type de données**, le **nom**et la **largeur** de la boîte de dialogue et, le cas échéant, la valeur du séparateur de date de Schema.ini.|  
|**Caractères**|**ANSI** ou **OEM**. OEM spécifie un jeu de caractères non-ANSI. La valeur par défaut est OEM si le format de l’élément sélectionné dans la liste **tables** n’a pas été précédemment défini par cette boîte de dialogue.|  
|**En-tête de nom de colonne**|Indique si les colonnes de la première ligne de la table sélectionnée doivent être utilisées comme noms de colonnes. **True** ou **false**. La valeur par défaut est FALSe si le format de l’élément sélectionné dans la liste **tables** n’a pas été précédemment défini par cette boîte de dialogue.|  
|**Colonnes**|Répertorie les noms de colonnes pour chaque colonne de la table sélectionnée. L’ordre des colonnes reflète l’ordre des colonnes dans la table. Cette liste est activée si un fichier a été sélectionné dans la liste **tables** .|  
|**Type de données**|Peut être de type BIT, BYTE, CHAR, CURRENCY, DATE, FLOAT, INTEGER, LONGCHAR, SHORT ou SINGLE. Les types de données de date peuvent être dans les formats suivants : « jj-mmm-AA », « mm-jj-aa », « mmm-jj-aa », « yyyy-mm-jj » ou « yyyy-mmm-jj ». « mm » désigne les nombres pour les mois ; « mmm » désigne des lettres pour les mois.|  
|**Délimiteur**|Spécifie le caractère délimiteur personnalisé à utiliser pour séparer les colonnes. Activé lorsque le format **personnalisé délimité** est sélectionné. Le délimiteur ne peut comporter qu’un seul caractère et les guillemets doubles (") ne peuvent pas être utilisés comme caractère délimiteur. (Le délimiteur ne peut pas être spécifié au format hexadécimal ou décimal.)|  
|**Format**|Délimité ou longueur fixe. Si délimité, indique le type de délimiteur utilisé : virgule (CSV), tabulation ou caractère spécial (personnalisé). La valeur par défaut est **délimité par CSV** si le format de l’élément sélectionné dans la liste **tables** n’a pas été précédemment défini par cette boîte de dialogue.<br /><br /> Si le **format** est de longueur fixe et que l' **en-tête de nom de colonne** a la valeur true, la première ligne doit être délimitée par des virgules.|  
|**Découverte**|Génère automatiquement les valeurs du type de données, du nom et de la largeur de la colonne pour les colonnes de la table sélectionnée en analysant le contenu de la table en fonction de la sélection de la zone de **format** . Activé lorsque le format de table est délimité. Toutes les colonnes définies précédemment dans la liste des **colonnes** sont effacées et remplacées par de nouvelles entrées. Si l' **en-tête de nom de colonne** n’est pas sélectionné, les noms de colonne sont générés automatiquement en tant que « F1 », « F2 », et ainsi de suite. Aucune valeur par défaut n’est affichée dans la zone **type de données** .<br /><br /> Cette fonctionnalité fonctionne uniquement sur les colonnes qui sont inférieures à 64 513 octets.|  
|**Modify**|Modifie la colonne sélectionnée à l’aide des valeurs du **type de données**, du **nom**et de la **largeur**.|  
|**Nom**|Affiche le nom de la colonne sélectionnée. Peut être utilisé pour spécifier un nouveau nom de colonne pour une colonne existante ou une nouvelle colonne.<br /><br /> Si l' **en-tête de nom de colonne** a la valeur true, le nom de colonne affiché est ignoré.|  
|**Remove**|Supprime la colonne sélectionnée.|  
|**Lignes à analyser**|Nombre de lignes que le programme d’installation ou le pilote analysera lors de la définition des colonnes et des types de données de colonne en fonction des données existantes.<br /><br /> Vous pouvez entrer un nombre compris entre 1 et 32767 pour le nombre de lignes à analyser. La valeur par défaut est 25 si le format de l’élément sélectionné dans la liste **tables** n’a pas été précédemment défini par cette boîte de dialogue. (Un nombre en dehors de la limite renverra une erreur.)|  
|**Tables**|Contient une liste de tous les fichiers du répertoire sélectionné dans la boîte de dialogue **configuration du texte** qui correspondent à la liste des extensions spécifiées.<br /><br /> Lorsque \<default> est sélectionné et que l’une des conditions suivantes est vraie, les valeurs des attributs de la table dans le groupe **tables** sont écrites dans Schema.ini (aucune autre entrée de Schema.ini n’est touchée) :<br /><br /> -Il n’existe aucun Schema.ini dans le répertoire spécifié.<br />-Le fichier Schema.ini existe, mais il n’existe aucune section dans Schema.ini pour l’un des fichiers texte (avec l’extension spécifiée) dans le répertoire.<br />-La section d’un fichier texte existe dans Schema.ini, mais le corps est vide.<br /><br /> Lorsque \<default> est sélectionné, le groupe de **colonnes** est désactivé.|  
|**Width**|La largeur de la colonne peut être modifiée pour les colonnes CHAR ou LONGCHAR. La largeur par défaut est 1 si le format de l’élément sélectionné dans la liste **tables** n’a pas été précédemment défini par cette boîte de dialogue.<br /><br /> Pour les autres types de données, le contrôle width est désactivé et aucune valeur n’est affichée.|
