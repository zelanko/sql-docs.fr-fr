---
title: Notes de publication pour le pilote OLE DB
description: Cet article de notes de publication décrit les changements de chaque version du pilote Microsoft OLE DB pour SQL Server.
ms.date: 02/27/2020
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 70f3239f1e644850bc391a0be5ef8918e1e9e617
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81727966"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Notes de publication de Microsoft OLE DB Driver pour SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Cette page décrit ce qui a été ajouté dans chaque version de Microsoft OLE DB Driver pour SQL Server.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1830"></a>18.3.0

![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x64](https://go.microsoft.com/fwlink/?linkid=2117515)  
![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x86](https://go.microsoft.com/fwlink/?linkid=2117517)  

Publication : 2 octobre 2019

Si vous avez besoin de télécharger le programme d’installation dans une langue autre que celle détectée pour vous, vous pouvez utiliser ces liens directs.  
Pour le pilote x64 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2117515&clcid=0x40a)  
Pour le pilote x86 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2117517&clcid=0x40a)  

### <a name="features-added"></a>Ajout de fonctionnalités

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge de l’authentification Azure Active Directory (`ActiveDirectoryInteractive`, `ActiveDirectoryMSI`). | [Utilisation d’Azure Active Directory](features/using-azure-active-directory.md). |
| Inclure la bibliothèque d’authentification Azure Active Directory (adal.dll) dans le programme d’installation | Maintenant inclus dans l’installation du pilote de base, le programme d’installation OLE DB met à niveau les installations existantes de la Bibliothèque d’authentification Microsoft Active Directory pour SQL Server et les supprime de la liste des applications installées dans Windows. |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Bogues corrigés

| Bogue corrigé | Détails |
| :-------- | :------ |
| Correction de la logique de suppression d’index dans [IIndexDefinition::DropIndex](https://go.microsoft.com/fwlink/?linkid=2106448). | Les versions précédentes du pilote OLE DB ne peuvent pas supprimer un index de clé primaire lorsque l’ID de schéma et l’ID d’utilisateur du propriétaire de l’index ne sont pas égaux. |
| &nbsp; | &nbsp; |

## <a name="previous-releases"></a>Versions précédentes

Téléchargez les versions précédentes du pilote OLE DB en cliquant sur les liens de téléchargement dans les sections suivantes :

## <a name="1823"></a>18.2.3

![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x64](https://go.microsoft.com/fwlink/?linkid=2119554)  
![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x86](https://go.microsoft.com/fwlink/?linkid=2119738)  

Publication : Juin 2019

Si vous avez besoin de télécharger le programme d’installation dans une langue autre que celle détectée pour vous, vous pouvez utiliser ces liens directs.  
Pour le pilote x64 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2119554&clcid=0x40a)  
Pour le pilote x86 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2119738&clcid=0x40a)  

### <a name="features-added-in-1823"></a>Fonctionnalités ajoutées dans la version 18.2.3

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge des mises à niveau du pilote à partir du média amovible SQL Server. | Cette amélioration permet de mettre à niveau les pilotes directement à partir du média amovible SQL Server. |
| &nbsp; | &nbsp; |

## <a name="1822"></a>18.2.2

![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x64](https://go.microsoft.com/fwlink/?linkid=2118512)  
![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x86](https://go.microsoft.com/fwlink/?linkid=2118415)  

Publication : Mai 2019

Si vous avez besoin de télécharger le programme d’installation dans une langue autre que celle détectée pour vous, vous pouvez utiliser ces liens directs.  
Pour le pilote x64 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2118512&clcid=0x40a)  
Pour le pilote x86 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2118415&clcid=0x40a)  

### <a name="bugs-fixed-in-1822"></a>Bogues corrigés dans la version 18.2.2

| Bogue corrigé | Détails |
| :-------- | :------ |
| Correction de l’authentification Azure Active Directory non interactive dans le multithread cloisonné (MTA). | OLE DB Driver 18.2.1 essaie de manière inappropriée de changer le modèle de concurrence COM sur un cloisonnement précédemment initialisé comme multithread (MTA). Par conséquent, dans une application qui effectue plusieurs appels à la suite à [CoInitialize](https://go.microsoft.com/fwlink/?linkid=2092520) ou [CoInitializeEx](https://go.microsoft.com/fwlink/?linkid=2092521) avant d’appeler l’interface [IDBInitialize::Initialize](https://go.microsoft.com/fwlink/?linkid=2092522), le pilote ne parvient pas à se connecter à l’aide des modes d’authentification Azure Active Directory. |
| &nbsp; | &nbsp; |

## <a name="1821"></a>18.2.1

![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x64](https://go.microsoft.com/fwlink/?linkid=2118511)  
![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x86](https://go.microsoft.com/fwlink/?linkid=2118278)  

Publication : Février 2019

Si vous avez besoin de télécharger le programme d’installation dans une langue autre que celle détectée pour vous, vous pouvez utiliser ces liens directs.  
Pour le pilote x64 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2118511&clcid=0x40a)  
Pour le pilote x86 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2118278&clcid=0x40a)  

### <a name="features-added-in-1821"></a>Fonctionnalités ajoutées dans la version 18.2.1

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge de l’encodage serveur UTF-8. | [Prise en charge d’UTF-8 dans OLE DB Driver pour SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Prise en charge de l’authentification Azure Active Directory. | [Utilisation d’Azure Active Directory](features/using-azure-active-directory.md). |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x64](https://go.microsoft.com/fwlink/?linkid=2118506)  
![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x86](https://go.microsoft.com/fwlink/?linkid=2118509)  

Publication : Juillet 2018

Si vous avez besoin de télécharger le programme d’installation dans une langue autre que celle détectée pour vous, vous pouvez utiliser ces liens directs.  
Pour le pilote x64 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2118506&clcid=0x40a)  
Pour le pilote x86 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2118509&2118509=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2118509&clcid=0x40a)  

### <a name="features-added-in-1810"></a>Fonctionnalités ajoutées dans la version 18.1.0

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge du mot clé de chaîne de connexion `UseFMTONLY` et de la propriété d’initialisation `SSPROP_INIT_USEFMTONLY`. | `UseFMTONLY` contrôle la façon dont les métadonnées sont récupérées pendant la connexion à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et les versions ultérieures.<br/><br/>Pour plus d'informations, consultez les pages suivantes : [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed-in-1810"></a>Bogues corrigés dans la version 18.1.0

| Bogue corrigé | Détails |
| :-------- | :------ |
| Correction d’une version incorrecte du fichier de format BCP. | OLE DB Driver 18.0 définit de manière inappropriée la version du fichier de format BCP sur 18.0 au lieu de 11.0.<br/>Les fichiers de format générés par OLE DB Driver 18.0 ne peuvent pas être lus par OLE DB Driver 18.1.<br/>Si vous devez utiliser des fichiers de format générés par la version précédente du pilote avec le nouveau pilote, vous pouvez modifier manuellement les fichiers pour remplacer la version par 11.0. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x64](https://go.microsoft.com/fwlink/?linkid=2118504)  
![Télécharger](../../ssms/media/download-icon.png) [Télécharger le programme d’installation x86](https://go.microsoft.com/fwlink/?linkid=2118277)  

Publication : Mars 2018

Si vous avez besoin de télécharger le programme d’installation dans une langue autre que celle détectée pour vous, vous pouvez utiliser ces liens directs.  
Pour le pilote x64 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2118504&clcid=0x40a)  
Pour le pilote x86 : [Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2118277&clcid=0x40a)  

### <a name="features-added-in-1802"></a>Fonctionnalités ajoutées dans la version 18.0.2

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge du mot clé de chaîne de connexion `MultiSubnetFailover` et de la propriété d’initialisation `SSPROP_INIT_MULTISUBNETFAILOVER`. | Pour plus d'informations, consultez les pages suivantes :<br/>&bull; &nbsp; [Prise en charge de la reprise d’activité et de la haute disponibilité par OLE DB Driver pour SQL Server](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md),<br/>&bull; &nbsp; [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Voir aussi

[Microsoft OLE DB Driver pour SQL Server](oledb-driver-for-sql-server.md)
