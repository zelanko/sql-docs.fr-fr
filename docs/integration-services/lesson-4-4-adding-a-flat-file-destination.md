---
title: 'Étape 4 : Ajouter une destination de fichier plat | Microsoft Docs'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 9bdb25380e74039a7ba62a89d4b1ba9c6d794d9f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055798"
---
# <a name="lesson-4-4-add-a-flat-file-destination"></a>Leçon 4-4 : Ajouter une destination de fichier plat

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



La sortie d’erreur de la transformation Lookup Currency Key réachemine toutes les lignes de données ayant échoué au cours de la recherche vers l’opération de transformation Script. Pour fournir davantage d’informations sur les erreurs survenues, la transformation Script exécute un script chargé d’obtenir la description de chaque erreur.  
  
Au cours de cette tâche, vous enregistrez toutes ces informations sur les lignes échouées dans un fichier texte délimité pour les traiter ultérieurement. Pour enregistrer les lignes ayant échoué, vous ajoutez et configurez un gestionnaire de connexions de fichiers plats pour le fichier texte qui contient les données sur les erreurs ainsi qu’une destination de fichier plat. En définissant les propriétés du gestionnaire de connexions de fichier plat utilisé par la destination de fichier plat, vous pouvez spécifier la façon dont elle met en forme et écrit le fichier texte. Pour plus d’informations, consultez [Gestionnaire de connexions de fichiers plats](../integration-services/connection-manager/flat-file-connection-manager.md) et [Destination de fichier plat](../integration-services/data-flow/flat-file-destination.md).  
  
## <a name="add-and-configure-a-flat-file-destination"></a>Ajouter et configurer une destination de fichier plat  
  
1.  Sélectionnez l’onglet **Flux de données**.  
  
2.  Dans la **Boîte à outils SSIS**, développez **Autres destinations**, puis faites glisser **Destination du fichier plat** sur l’aire de conception Flux de données. Placez la **Destination de fichier plat** directement sous la transformation **Get Error Description** .  
  
3.  Sélectionnez la transformation **Obtenir la description de l’erreur**, puis faites glisser la flèche bleue vers la nouvelle **Destination de fichier plat**.  
  
4.  Sur l’aire de conception **Flux de données**, sélectionnez le nom **Destination de fichier plat** dans la nouvelle transformation de **Destination de fichier plat**, puis remplacez ce nom par **Failed Rows**.  
  
5.  Cliquez avec le bouton droit sur la transformation **Failed Rows**, sélectionnez **Modifier**, puis dans l’**Éditeur de destination de fichier plat**, sélectionnez **Nouveau**.  
  
6.  Dans la boîte de dialogue **Format de fichier plat**, assurez-vous que **Délimité** est sélectionné, puis sélectionnez **OK**.  
  
7.  Dans l’**Éditeur du gestionnaire de connexions de fichiers plats**, dans la zone **Nom du gestionnaire de connexions**, entrez *Données d’erreur*.  
  
8.  Dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats**, sélectionnez **Parcourir**, puis recherchez le dossier dans lequel le fichier est à stocker.  
  
9. Dans la boîte de dialogue **Ouvrir**, dans la zone **Nom de fichier**, entrez *SortieErreur.txt*, puis sélectionnez **Ouvrir**.  
  
10. Dans la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers plats**, vérifiez que **Paramètres régionaux** a pour valeur **Anglais (États-Unis)** et que la zone **Page de codes** a pour valeur **1252 (ANSI-Latin I)** .  
  
11. Dans le volet Options, sélectionnez **Colonnes**.  
  
    En plus des colonnes du fichier de données source, il existe trois nouvelles colonnes : ErrorCode, ErrorColumn et ErrorDescription. Ces colonnes représentent la sortie d’erreur de la transformation Lookup Currency Key et le script de la transformation Get Error Description. Vous pouvez utiliser ces colonnes pour résoudre le problème à l’origine de l’échec de la ligne.  
  
12. Sélectionnez **OK**.  
  
13. Dans l' **Éditeur de destination de fichier plat**, désactivez la case à cocher **Remplacer les données du fichier** .  
  
    Le fait de décocher cette case conserve les erreurs sur plusieurs exécutions de packages en ajoutant la sortie d’erreur de chaque nouvelle exécution.
  
14. Dans l’**Éditeur de destination de fichier plat**, sélectionnez **Mappages** pour vérifier que toutes les colonnes sont correctes. Vous pouvez également renommer les colonnes dans la destination.  
  
15. Sélectionnez **OK**.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante
[Étape 5 : Tester le package du tutoriel de la leçon 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  
  
