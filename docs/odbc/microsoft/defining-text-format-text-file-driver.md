---
title: Définition du Format de texte (pilote de fichier texte) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00d20f8a6dd4d79b3100549d9286e7534bc8ce6e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63240381"
---
# <a name="defining-text-format-text-file-driver"></a>Définition du format du texte (pilote de fichier texte)
Lorsque le pilote de texte est utilisé, vous pouvez utiliser la **définition du Format texte** boîte de dialogue pour définir le format pour les colonnes dans un fichier sélectionné. Cette boîte de dialogue vous permet de spécifier le schéma pour chaque table de données. Ces informations sont écrit dans un fichier Schema.ini dans le répertoire de source de données. Un fichier Schema.ini distinct est créé pour chaque répertoire de source de données de texte.  
  
> [!NOTE]  
>  Le même format de fichier par défaut s’applique à toutes les nouvelles tables de données de texte. Tous les fichiers créés par l’instruction CREATE TABLE héritent de ces mêmes valeurs de format par défaut, qui sont définis en sélectionnant les valeurs de format de fichier dans le **définition du Format texte** boîte de dialogue avec \<par défaut > choisi dans la **Tables** liste. Le pilote de texte ne modifie pas le format d’un fichier texte existant pour correspondre au format défini dans cette boîte de dialogue, mais retourne une erreur lorsqu’il utilise le format, comme lorsqu’il tente de récupérer des données à partir du fichier texte.  
  
 Les options suivantes sont disponibles dans le **définition du Format texte** boîte de dialogue :  
  
|Option|Informations|  
|------------|-----------------|  
|**Ajouter**|Ajoute une colonne en utilisant les valeurs dans **Type de données**, **nom**, et **largeur** à partir de la boîte de dialogue, et si applicable, le séparateur de Date valeur Schema.ini.|  
|**Caractères**|**ANSI** ou **OEM**. OEM spécifie un jeu de caractères non-ANSI. L’emplacement par défaut pour les OEM si le format de l’élément sélectionné dans le **Tables** liste n’a pas été précédemment définie par cette boîte de dialogue.|  
|**En-tête de nom de colonne**|Indique si les colonnes de la première ligne de la table sélectionnée doivent être utilisés comme noms de colonne. Soit **TRUE** ou **FALSE**. Valeur par défaut est FALSE si le format de l’élément sélectionné dans le **Tables** liste n’a pas été précédemment définie par cette boîte de dialogue.|  
|**Colonnes**|Répertorie les noms de colonne pour chaque colonne dans la table sélectionnée. L’ordre des colonnes reflète l’ordre des colonnes dans la table. Cette liste est activée si un fichier a été sélectionné dans le **Tables** liste.|  
|**Type de données**|Peut être BIT, BYTE, CHAR, devise, DATE, FLOAT, entier, LONGCHAR, SHORT ou unique. Types de données de date peuvent être dans les formats suivants : « jj-mmm-aa », « mm-jj-aa », « mmm jj-aa », « aaaa-mm-jj » ou « aaaa-mmm-jj ». « mm » désigne les numéros de mois ; « mmm » désigne des lettres pour le mois.|  
|**Delimiter**|Spécifie le caractère délimiteur personnalisé à utiliser pour séparer les colonnes. Lorsque le **personnalisé délimitée par des** format est sélectionné. Le délimiteur peut être qu’un seul caractère de longueur et guillemets doubles (") ne peut pas servir en tant que le caractère délimiteur. (Le délimiteur ne peut pas être spécifié au format hexadécimal ou décimal).|  
|**Format**|Longueur fixe ou délimité. S’ils sont délimités, indique le type de délimiteur utilisé : une virgule (CSV), onglet ou un caractère spécial (personnalisé). Par défaut est **délimitation CSV** si le format de l’élément sélectionné dans le **Tables** liste n’a pas été précédemment définie par cette boîte de dialogue.<br /><br /> Si **Format** est de longueur fixe et **en-tête de nom de colonne** est TRUE, la première ligne doit être délimitée par des virgules.|  
|**Estimation**|Génère automatiquement des valeurs de type, nom et la largeur de données pour les colonnes de la colonne dans la table sélectionnée en analysant le contenu de la table en fonction de la **Format** zone de sélection. Activé quand le format de table est délimité. Toute définie précédemment des colonnes dans le **colonnes** liste sont effacées et remplacées par nouvelles entrées. Si **en-tête de nom de colonne** est ne pas sélectionnée, les noms de colonne sont générés automatiquement en tant que « F1 », « F2 » et ainsi de suite. Aucune valeur par défaut n’est affichée dans le **Type de données** boîte.<br /><br /> Cette fonctionnalité fonctionne uniquement sur les colonnes qui sont inférieures à 64 513 octets.|  
|**Modifier**|Modifie la colonne sélectionnée en utilisant les valeurs dans **Type de données**, **nom**, et **largeur**.|  
|**Nom**|Affiche le nom de la colonne sélectionnée. Peut être utilisé pour spécifier un nouveau nom de colonne pour une colonne existante ou une nouvelle colonne.<br /><br /> Si **en-tête de nom de colonne** a la valeur TRUE, la colonne nom affiché est ignoré.|  
|**Supprimer**|Supprime la colonne sélectionnée.|  
|**Lignes à balayer**|Le nombre de lignes que le programme d’installation ou le pilote analysera lors de la définition des colonnes et types de données de colonne en fonction des données existantes.<br /><br /> Vous pouvez entrer un nombre compris entre 1 et 32 767 pour le nombre de lignes à analyser. Par défaut, cette fonction 25 si le format de l’élément sélectionné dans le **Tables** liste n’a pas été précédemment définie par cette boîte de dialogue. (Un nombre en dehors de la limite retournera une erreur).|  
|**Tables**|Contient une liste de tous les fichiers dans le répertoire sélectionné dans le **le programme d’installation de texte** boîte de dialogue qui correspondent à la liste des extensions spécifiées.<br /><br /> Lorsque \<par défaut > est sélectionnée, et une des opérations suivantes est true, les valeurs des attributs de table dans le **Tables** groupe sont écrits dans Schema.ini (sans les autres entrées dans Schema.ini sont couvertes) :<br /><br /> -Il n’existe aucun Schema.ini dans le répertoire spécifié.<br />-Le fichier Schema.ini existe, mais il n’existe pas dans Schema.ini pour un des fichiers texte (avec l’extension spécifiée) dans le répertoire.<br />-La section d’un fichier texte existe dans Schema.ini, mais le corps est vide.<br /><br /> Lorsque \<par défaut > est sélectionnée, le **colonnes** groupe est désactivé.|  
|**Width**|La largeur de la colonne peut être modifiée pour les colonnes CHAR ou LONGCHAR. La largeur par défaut est 1 si le format de l’élément sélectionné dans le **Tables** liste n’a pas été précédemment définie par cette boîte de dialogue.<br /><br /> Pour les autres types de données, la largeur du contrôle est désactivé et aucune valeur n’est affichée.|
