---
title: Informations de référence sur les API du portail d’appareil
description: Informations de référence sur l’API pour le portail de périphériques Windows sur HoloLens
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, portail des appareils Windows, API, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 1085f6c948ab7fe0ff8cb3801ebb0b883570acbc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677968"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="2ca14-104">Informations de référence sur les API du portail d’appareil</span><span class="sxs-lookup"><span data-stu-id="2ca14-104">Device portal API reference</span></span>

<span data-ttu-id="2ca14-105">Tout ce qui se trouve dans le [portail de périphériques Windows](using-the-windows-device-portal.md) repose sur des API REST que vous pouvez utiliser pour accéder aux données et contrôler votre appareil par programme.</span><span class="sxs-lookup"><span data-stu-id="2ca14-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="2ca14-106">Déploiement de l’application</span><span class="sxs-lookup"><span data-stu-id="2ca14-106">App deloyment</span></span>

<span data-ttu-id="2ca14-107">**/API/App/packagemanager/package (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="2ca14-108">Désinstalle une application</span><span class="sxs-lookup"><span data-stu-id="2ca14-108">Uninstalls an app</span></span>

<span data-ttu-id="2ca14-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-109">Parameters</span></span>
* <span data-ttu-id="2ca14-110">Package : nom de fichier du package à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="2ca14-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="2ca14-111">**/API/App/packagemanager/package (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="2ca14-112">Installe une application</span><span class="sxs-lookup"><span data-stu-id="2ca14-112">Installs an App</span></span>

<span data-ttu-id="2ca14-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-113">Parameters</span></span>
* <span data-ttu-id="2ca14-114">Package : nom de fichier du package à installer.</span><span class="sxs-lookup"><span data-stu-id="2ca14-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="2ca14-115">Payload</span><span class="sxs-lookup"><span data-stu-id="2ca14-115">Payload</span></span>
* <span data-ttu-id="2ca14-116">corps http en plusieurs parties, conforme</span><span class="sxs-lookup"><span data-stu-id="2ca14-116">multi-part conforming http body</span></span>

<span data-ttu-id="2ca14-117">**/API/App/packagemanager/packages (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="2ca14-118">Récupère la liste des applications installées sur le système, avec les détails</span><span class="sxs-lookup"><span data-stu-id="2ca14-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="2ca14-119">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-119">Return data</span></span>
* <span data-ttu-id="2ca14-120">Liste des packages installés avec des détails</span><span class="sxs-lookup"><span data-stu-id="2ca14-120">List of installed packages with details</span></span>

<span data-ttu-id="2ca14-121">**/API/App/packagemanager/State (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="2ca14-122">Obtient l’état de l’installation de l’application en cours</span><span class="sxs-lookup"><span data-stu-id="2ca14-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="2ca14-123">Collection de vidages</span><span class="sxs-lookup"><span data-stu-id="2ca14-123">Dump collection</span></span>

<span data-ttu-id="2ca14-124">**/API/Debug/dump/usermode/CrashControl (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="2ca14-125">Désactive la collecte de vidages sur incident pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="2ca14-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="2ca14-126">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-126">Parameters</span></span>
* <span data-ttu-id="2ca14-127">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="2ca14-127">packageFullname : package name</span></span>

<span data-ttu-id="2ca14-128">**/API/Debug/dump/usermode/CrashControl (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="2ca14-129">Obtient les paramètres de la collection de vidages sur incident des applications faisant</span><span class="sxs-lookup"><span data-stu-id="2ca14-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="2ca14-130">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-130">Parameters</span></span>
* <span data-ttu-id="2ca14-131">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="2ca14-131">packageFullname : package name</span></span>

<span data-ttu-id="2ca14-132">**/API/Debug/dump/usermode/CrashControl (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="2ca14-133">Active et définit les paramètres de contrôle de vidage pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="2ca14-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="2ca14-134">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-134">Parameters</span></span>
* <span data-ttu-id="2ca14-135">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="2ca14-135">packageFullname : package name</span></span>

<span data-ttu-id="2ca14-136">**/API/Debug/dump/usermode/crashdump (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="2ca14-137">Supprime un vidage sur incident pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="2ca14-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="2ca14-138">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-138">Parameters</span></span>
* <span data-ttu-id="2ca14-139">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="2ca14-139">packageFullname : package name</span></span>
* <span data-ttu-id="2ca14-140">fileName : nom du fichier dump</span><span class="sxs-lookup"><span data-stu-id="2ca14-140">fileName : dump file name</span></span>

<span data-ttu-id="2ca14-141">**/API/Debug/dump/usermode/crashdump (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="2ca14-142">Récupère un vidage sur incident pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="2ca14-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="2ca14-143">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-143">Parameters</span></span>
* <span data-ttu-id="2ca14-144">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="2ca14-144">packageFullname : package name</span></span>
* <span data-ttu-id="2ca14-145">fileName : nom du fichier dump</span><span class="sxs-lookup"><span data-stu-id="2ca14-145">fileName : dump file name</span></span>

<span data-ttu-id="2ca14-146">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-146">Return data</span></span>
* <span data-ttu-id="2ca14-147">Fichier dump.</span><span class="sxs-lookup"><span data-stu-id="2ca14-147">Dump file.</span></span> <span data-ttu-id="2ca14-148">Inspecter avec WinDbg ou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ca14-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="2ca14-149">**/API/Debug/dump/usermode/dumps (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="2ca14-150">Retourne la liste de tous les vidages sur incident pour les applications faisant</span><span class="sxs-lookup"><span data-stu-id="2ca14-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="2ca14-151">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-151">Return data</span></span>
* <span data-ttu-id="2ca14-152">Liste des vidages sur incident par application à chargement latéral</span><span class="sxs-lookup"><span data-stu-id="2ca14-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="2ca14-153">ETW</span><span class="sxs-lookup"><span data-stu-id="2ca14-153">ETW</span></span>

<span data-ttu-id="2ca14-154">**/API/ETW/Providers (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="2ca14-155">Énumère les fournisseurs inscrits</span><span class="sxs-lookup"><span data-stu-id="2ca14-155">Enumerates registered providers</span></span>

<span data-ttu-id="2ca14-156">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-156">Return data</span></span>
* <span data-ttu-id="2ca14-157">Liste des fournisseurs, nom convivial et GUID</span><span class="sxs-lookup"><span data-stu-id="2ca14-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="2ca14-158">**/API/ETW/session/Realtime (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="2ca14-159">Crée une session ETW en temps réel ; géré sur un WebSocket.</span><span class="sxs-lookup"><span data-stu-id="2ca14-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="2ca14-160">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-160">Return data</span></span>
* <span data-ttu-id="2ca14-161">Événements ETW des fournisseurs activés</span><span class="sxs-lookup"><span data-stu-id="2ca14-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="2ca14-162">Système d’exploitation holographique</span><span class="sxs-lookup"><span data-stu-id="2ca14-162">Holographic OS</span></span>

<span data-ttu-id="2ca14-163">**/API/Holographic/OS/ETW/customproviders (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="2ca14-164">Retourne une liste de fournisseurs ETW spécifiques à HoloLens qui ne sont pas inscrits auprès du système.</span><span class="sxs-lookup"><span data-stu-id="2ca14-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="2ca14-165">**/API/Holographic/OS/services (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="2ca14-166">Retourne les États de tous les services en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2ca14-166">Returns the states of all services running.</span></span>

<span data-ttu-id="2ca14-167">**/API/Holographic/OS/Settings/IPD (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="2ca14-168">Obtient la IPD stockée (distance interpupillary) en millimètres.</span><span class="sxs-lookup"><span data-stu-id="2ca14-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="2ca14-169">**/API/Holographic/OS/Settings/IPD (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="2ca14-170">Définit l’IPD</span><span class="sxs-lookup"><span data-stu-id="2ca14-170">Sets the IPD</span></span>

<span data-ttu-id="2ca14-171">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-171">Parameters</span></span>
* <span data-ttu-id="2ca14-172">IPD : nouvelle valeur IPD à définir en millimètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="2ca14-173">**/API/Holographic/OS/webmanagement/Settings/HTTPS (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="2ca14-174">Obtenir la spécification HTTPS pour Device Portal</span><span class="sxs-lookup"><span data-stu-id="2ca14-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="2ca14-175">**/API/Holographic/OS/webmanagement/Settings/HTTPS (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="2ca14-176">Définit les exigences HTTPs pour le portail de l’appareil</span><span class="sxs-lookup"><span data-stu-id="2ca14-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="2ca14-177">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-177">Parameters</span></span>
* <span data-ttu-id="2ca14-178">obligatoire : Oui, non ou par défaut</span><span class="sxs-lookup"><span data-stu-id="2ca14-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="2ca14-179">Perception holographique</span><span class="sxs-lookup"><span data-stu-id="2ca14-179">Holographic Perception</span></span>

<span data-ttu-id="2ca14-180">**/API/Holographic/perception/client (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="2ca14-181">Accepte les mises à niveau de WebSocket et exécute un client de perception qui envoie des mises à jour à 30 i/s.</span><span class="sxs-lookup"><span data-stu-id="2ca14-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="2ca14-182">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-182">Parameters</span></span>
* <span data-ttu-id="2ca14-183">Clientmode : "active" force le mode de suivi visuel lorsqu’il ne peut pas être établi passivement</span><span class="sxs-lookup"><span data-stu-id="2ca14-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="2ca14-184">Thermique holographique</span><span class="sxs-lookup"><span data-stu-id="2ca14-184">Holographic Thermal</span></span>

<span data-ttu-id="2ca14-185">**/API/Holographic/thermal/stage (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="2ca14-186">Récupération de l’étape thermique de l’appareil (0 normal, 1 chaud, 2 critique)</span><span class="sxs-lookup"><span data-stu-id="2ca14-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="2ca14-187">Map Manager</span><span class="sxs-lookup"><span data-stu-id="2ca14-187">Map Manager</span></span>

<span data-ttu-id="2ca14-188">**/api/holographic/mapmanager/mapFiles (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="2ca14-189">Obtient la liste des fichiers de mappage disponibles (. MapX).</span><span class="sxs-lookup"><span data-stu-id="2ca14-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="2ca14-190">**/api/holographic/mapmanager/anchorFiles (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="2ca14-191">Obtient la liste des fichiers d’ancrage disponibles (. ancx).</span><span class="sxs-lookup"><span data-stu-id="2ca14-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="2ca14-192">**/api/holographic/mapmanager/srdbFiles (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="2ca14-193">Obtient la liste des fichiers de base de données de reconstruction spatiale disponibles (. srdb).</span><span class="sxs-lookup"><span data-stu-id="2ca14-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="2ca14-194">**/API/Holographic/mapmanager/getanchors (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="2ca14-195">Obtient la liste des ancres persistantes pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="2ca14-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="2ca14-196">Télécharger/Télécharger/supprimer des fichiers</span><span class="sxs-lookup"><span data-stu-id="2ca14-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="2ca14-197">**/API/Holographic/mapmanager/Download (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="2ca14-198">Télécharge un fichier de base de données de carte, d’ancrage ou de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="2ca14-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="2ca14-199">Le fichier doit avoir été préalablement téléchargé ou exporté.</span><span class="sxs-lookup"><span data-stu-id="2ca14-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="2ca14-200">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-200">Parameters</span></span>
* <span data-ttu-id="2ca14-201">FileName : nom du fichier à télécharger.</span><span class="sxs-lookup"><span data-stu-id="2ca14-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="2ca14-202">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="2ca14-203">**/API/Holographic/mapmanager/upload (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="2ca14-204">Charge un fichier de base de données de carte, d’ancrage ou de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="2ca14-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="2ca14-205">Une fois qu’un fichier est chargé, il peut être importé ultérieurement pour être utilisé par le système.</span><span class="sxs-lookup"><span data-stu-id="2ca14-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="2ca14-206">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-206">Parameters</span></span>
* <span data-ttu-id="2ca14-207">fichier : nom du fichier à charger.</span><span class="sxs-lookup"><span data-stu-id="2ca14-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="2ca14-208">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="2ca14-209">**/API/Holographic/mapmanager/Delete (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="2ca14-210">Supprime un fichier de base de données de carte, d’ancrage ou de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="2ca14-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="2ca14-211">Le fichier doit avoir été préalablement téléchargé ou exporté.</span><span class="sxs-lookup"><span data-stu-id="2ca14-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="2ca14-212">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-212">Parameters</span></span>
* <span data-ttu-id="2ca14-213">FileName : nom du fichier à supprimer.</span><span class="sxs-lookup"><span data-stu-id="2ca14-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="2ca14-214">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="2ca14-215">Exporter</span><span class="sxs-lookup"><span data-stu-id="2ca14-215">Export</span></span>

<span data-ttu-id="2ca14-216">**/API/Holographic/mapmanager/Export (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="2ca14-217">Exporte le mappage actuellement utilisé par le système.</span><span class="sxs-lookup"><span data-stu-id="2ca14-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="2ca14-218">Une fois exportée, elle peut être téléchargée.</span><span class="sxs-lookup"><span data-stu-id="2ca14-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="2ca14-219">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="2ca14-220">**/API/Holographic/mapmanager/exportanchors (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="2ca14-221">Exporte le mappage actuellement utilisé par le système.</span><span class="sxs-lookup"><span data-stu-id="2ca14-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="2ca14-222">Une fois exportée, elle peut être téléchargée.</span><span class="sxs-lookup"><span data-stu-id="2ca14-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="2ca14-223">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="2ca14-224">**/API/Holographic/mapmanager/exportmapandanchors (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="2ca14-225">Exporte le mappage et les ancres actuellement utilisés par le système.</span><span class="sxs-lookup"><span data-stu-id="2ca14-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="2ca14-226">Une fois exportés, ils peuvent être téléchargés.</span><span class="sxs-lookup"><span data-stu-id="2ca14-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="2ca14-227">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="2ca14-228">**/API/Holographic/mapmanager/exportmapandspatialmappingdb (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="2ca14-229">Exporte le mappage et la base de données de reconstruction spatiale actuellement utilisés par le système.</span><span class="sxs-lookup"><span data-stu-id="2ca14-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="2ca14-230">Une fois qu’elles sont exportées, elles peuvent être téléchargées.</span><span class="sxs-lookup"><span data-stu-id="2ca14-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="2ca14-231">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="2ca14-232">Importer</span><span class="sxs-lookup"><span data-stu-id="2ca14-232">Import</span></span>

<span data-ttu-id="2ca14-233">**/API/Holographic/mapmanager/Import (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="2ca14-234">Indique au système le mappage qui doit être utilisé actuellement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="2ca14-235">Peut être appelé sur des fichiers qui ont été exportés ou téléchargés.</span><span class="sxs-lookup"><span data-stu-id="2ca14-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="2ca14-236">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-236">Parameters</span></span>
* <span data-ttu-id="2ca14-237">Nom de fichier : nom de la carte à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2ca14-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="2ca14-238">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="2ca14-239">**/API/Holographic/mapmanager/importanchors (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="2ca14-240">Indique au système les ancres à utiliser actuellement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="2ca14-241">Peut être appelé sur des fichiers qui ont été exportés ou téléchargés.</span><span class="sxs-lookup"><span data-stu-id="2ca14-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="2ca14-242">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-242">Parameters</span></span>
* <span data-ttu-id="2ca14-243">Nom de fichier : nom des ancres à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2ca14-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="2ca14-244">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="2ca14-245">**/API/Holographic/mapmanager/importspatialmappingdb (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="2ca14-246">Indique au système la base de données de reconstruction spatiale à utiliser actuellement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="2ca14-247">Peut être appelé sur des fichiers qui ont été exportés ou téléchargés.</span><span class="sxs-lookup"><span data-stu-id="2ca14-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="2ca14-248">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-248">Parameters</span></span>
* <span data-ttu-id="2ca14-249">Nom de fichier : nom de la base de connaissances de mappage spatiale à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2ca14-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="2ca14-250">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="2ca14-251">Autre</span><span class="sxs-lookup"><span data-stu-id="2ca14-251">Other</span></span>

<span data-ttu-id="2ca14-252">**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="2ca14-253">Réinitialisez le système pour la carte, les ancres et la base de données de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="2ca14-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="2ca14-254">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2ca14-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="2ca14-255">**/API/Holographic/mapmanager/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="2ca14-256">Obtient l’état du système, notamment les fichiers de base de données de mappage, d’ancrage et de reconstruction spatiale qui ont été importés pour la dernière fois.</span><span class="sxs-lookup"><span data-stu-id="2ca14-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="2ca14-257">MRC (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="2ca14-257">Mixed Reality Capture</span></span>

<span data-ttu-id="2ca14-258">**/API/Holographic/MRC/file (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="2ca14-259">Télécharge un fichier de réalité mixte à partir de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="2ca14-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="2ca14-260">Utilisez le paramètre de requête op = Stream pour la diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="2ca14-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="2ca14-261">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-261">Parameters</span></span>
* <span data-ttu-id="2ca14-262">nom de fichier : nom, hex64 encodé, du fichier vidéo à récupérer</span><span class="sxs-lookup"><span data-stu-id="2ca14-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="2ca14-263">OP : flux</span><span class="sxs-lookup"><span data-stu-id="2ca14-263">op : stream</span></span>

<span data-ttu-id="2ca14-264">**/API/Holographic/MRC/file (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="2ca14-265">Supprime un enregistrement de la réalité mixte de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="2ca14-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="2ca14-266">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-266">Parameters</span></span>
* <span data-ttu-id="2ca14-267">nom de fichier : nom, hex64 encodé, du fichier à supprimer</span><span class="sxs-lookup"><span data-stu-id="2ca14-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="2ca14-268">**/API/Holographic/MRC/Files (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="2ca14-269">Retourne la liste des fichiers de réalité mixte stockés sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="2ca14-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="2ca14-270">**/API/Holographic/MRC/photo (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="2ca14-271">Prend une photo de réalité mixte et crée un fichier sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="2ca14-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="2ca14-272">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-272">Parameters</span></span>
* <span data-ttu-id="2ca14-273">Holo : capturer les hologrammes : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="2ca14-274">PV : capturer l’appareil photo PV : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="2ca14-275">RenderFromCamera : (HoloLens 2 uniquement) rendu du point de vue de la caméra photo/vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="2ca14-276">**/API/Holographic/MRC/Settings (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="2ca14-277">Obtient les paramètres de capture de la réalité mixte par défaut</span><span class="sxs-lookup"><span data-stu-id="2ca14-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="2ca14-278">**/API/Holographic/MRC/Settings (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="2ca14-279">Définit les paramètres de capture de la réalité mixte par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ca14-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="2ca14-280">Certains de ces paramètres sont appliqués à la photo et à la capture de vidéo MRC du système.</span><span class="sxs-lookup"><span data-stu-id="2ca14-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="2ca14-281">**/API/Holographic/MRC/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="2ca14-282">Obtient l’état de capture de la réalité mixte dans le portail de périphériques Windows.</span><span class="sxs-lookup"><span data-stu-id="2ca14-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="2ca14-283">\**_Réponse_* _</span><span class="sxs-lookup"><span data-stu-id="2ca14-283">\**_Response_* _</span></span>

<span data-ttu-id="2ca14-284">La réponse contient une propriété JSON indiquant si le portail de périphériques Windows enregistre ou non une vidéo.</span><span class="sxs-lookup"><span data-stu-id="2ca14-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="2ca14-285">_ */API/Holographic/MRC/thumbnail (récupération)*\*</span><span class="sxs-lookup"><span data-stu-id="2ca14-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="2ca14-286">Obtient l’image miniature pour le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="2ca14-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="2ca14-287">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-287">Parameters</span></span>
* <span data-ttu-id="2ca14-288">nom de fichier : nom, hex64 encodé, du fichier pour lequel la miniature est demandée.</span><span class="sxs-lookup"><span data-stu-id="2ca14-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="2ca14-289">**/API/Holographic/MRC/Video/Control/Start (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="2ca14-290">Démarre un enregistrement de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="2ca14-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="2ca14-291">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-291">Parameters</span></span>
* <span data-ttu-id="2ca14-292">Holo : capturer les hologrammes : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="2ca14-293">PV : capturer l’appareil photo PV : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="2ca14-294">MIC : capturer le microphone : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="2ca14-295">loopback : capturer l’audio de l’application : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="2ca14-296">RenderFromCamera : (HoloLens 2 uniquement) rendu du point de vue de la caméra photo/vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="2ca14-297">Vstab : (HoloLens 2 uniquement) activer la stabilisation vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="2ca14-298">vstabbuffer : (HoloLens 2 uniquement) latence de la mémoire tampon de stabilisation vidéo : de 0 à 30 frames (15 images par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="2ca14-299">**/API/Holographic/MRC/Video/Control/Stop (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="2ca14-300">Arrête l’enregistrement de la réalité mixte actuelle</span><span class="sxs-lookup"><span data-stu-id="2ca14-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="2ca14-301">Diffusion en continu de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="2ca14-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="2ca14-302">HoloLens prend en charge l’aperçu instantané de la réalité mixte via le téléchargement segmenté d’un MP4 fragmenté.</span><span class="sxs-lookup"><span data-stu-id="2ca14-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="2ca14-303">Les flux de réalité mixte partagent le même ensemble de paramètres pour contrôler ce qui est capturé :</span><span class="sxs-lookup"><span data-stu-id="2ca14-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="2ca14-304">Holo : capturer les hologrammes : true ou false</span><span class="sxs-lookup"><span data-stu-id="2ca14-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="2ca14-305">PV : capturer l’appareil photo PV : true ou false</span><span class="sxs-lookup"><span data-stu-id="2ca14-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="2ca14-306">MIC : capturer le microphone : true ou false</span><span class="sxs-lookup"><span data-stu-id="2ca14-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="2ca14-307">loopback : capturer l’audio de l’application : true ou false</span><span class="sxs-lookup"><span data-stu-id="2ca14-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="2ca14-308">Si aucun de ces éléments n’est spécifié : les hologrammes, la caméra photo/vidéo et l’audio de l’application sont capturés</span><span class="sxs-lookup"><span data-stu-id="2ca14-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="2ca14-309">Si des paramètres sont spécifiés : les paramètres non spécifiés ont par défaut la valeur false</span><span class="sxs-lookup"><span data-stu-id="2ca14-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="2ca14-310">Paramètres facultatifs (HoloLens 2 uniquement)</span><span class="sxs-lookup"><span data-stu-id="2ca14-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="2ca14-311">RenderFromCamera : rendu du point de vue de la caméra photo/vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="2ca14-312">Vstab : activer la stabilisation vidéo : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="2ca14-313">vstabbuffer : latence de la mémoire tampon de stabilisation vidéo : de 0 à 30 frames (15 images par défaut)</span><span class="sxs-lookup"><span data-stu-id="2ca14-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="2ca14-314">**/API/Holographic/Stream/live.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="2ca14-315">Un flux 1280x720p 30fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="2ca14-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="2ca14-316">**/API/Holographic/Stream/live_high.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="2ca14-317">Un flux 1280x720p 30fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="2ca14-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="2ca14-318">**/API/Holographic/Stream/live_med.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="2ca14-319">Flux 854x480p 30fps 2,5 Mbits.</span><span class="sxs-lookup"><span data-stu-id="2ca14-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="2ca14-320">**/API/Holographic/Stream/live_low.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="2ca14-321">Flux 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="2ca14-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="2ca14-322">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="2ca14-322">Networking</span></span>

<span data-ttu-id="2ca14-323">**/API/Networking/ipconfig (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="2ca14-324">Obtient la configuration IP actuelle</span><span class="sxs-lookup"><span data-stu-id="2ca14-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="2ca14-325">Informations sur le système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="2ca14-325">OS Information</span></span>

<span data-ttu-id="2ca14-326">**/API/OS/info (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="2ca14-327">Obtient des informations sur le système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="2ca14-327">Gets operating system information</span></span>

<span data-ttu-id="2ca14-328">**/API/OS/MachineName (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="2ca14-329">Obtient le nom de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="2ca14-329">Gets the machine name</span></span>

<span data-ttu-id="2ca14-330">**/API/OS/MachineName (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="2ca14-331">Définit le nom de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="2ca14-331">Sets the machine name</span></span>

<span data-ttu-id="2ca14-332">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-332">Parameters</span></span>
* <span data-ttu-id="2ca14-333">nom : nouveau nom de l’ordinateur, hex64 encodé, à affecter à</span><span class="sxs-lookup"><span data-stu-id="2ca14-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="2ca14-334">Contrôle de simulation de perception</span><span class="sxs-lookup"><span data-stu-id="2ca14-334">Perception Simulation Control</span></span>

<span data-ttu-id="2ca14-335">**/API/Holographic/simulation/Control/mode (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="2ca14-336">Obtient le mode de simulation</span><span class="sxs-lookup"><span data-stu-id="2ca14-336">Get the simulation mode</span></span>

<span data-ttu-id="2ca14-337">**/API/Holographic/simulation/Control/mode (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="2ca14-338">Définir le mode de simulation</span><span class="sxs-lookup"><span data-stu-id="2ca14-338">Set the simulation mode</span></span>

<span data-ttu-id="2ca14-339">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-339">Parameters</span></span>
* <span data-ttu-id="2ca14-340">mode : mode de simulation : par défaut, simulation, distant, hérité</span><span class="sxs-lookup"><span data-stu-id="2ca14-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="2ca14-341">**/API/Holographic/simulation/Control/Stream (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="2ca14-342">Supprimer un flux de contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ca14-342">Delete a control stream.</span></span>

<span data-ttu-id="2ca14-343">**/API/Holographic/simulation/Control/Stream (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="2ca14-344">Ouvrez une connexion de socket Web pour un flux de contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ca14-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="2ca14-345">**/API/Holographic/simulation/Control/Stream (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="2ca14-346">Créez un flux de contrôle (priorité obligatoire) ou publiez des données dans un flux créé (streamId requis).</span><span class="sxs-lookup"><span data-stu-id="2ca14-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="2ca14-347">Les données publiées sont supposées être de type « application/octet-stream ».</span><span class="sxs-lookup"><span data-stu-id="2ca14-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="2ca14-348">**/API/Holographic/Simulation/Display/Stream (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="2ca14-349">Demandez un flux vidéo de simulation contenant le contenu affiché sur le système lorsqu’il est en mode « simulation ».</span><span class="sxs-lookup"><span data-stu-id="2ca14-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="2ca14-350">Un en-tête de descripteur de format simple sera envoyé initialement, suivi des textures encodées H. 264, chacune précédée d’un en-tête indiquant l’index oculaire et la taille de la texture.</span><span class="sxs-lookup"><span data-stu-id="2ca14-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="2ca14-351">Lecture de simulation de perception</span><span class="sxs-lookup"><span data-stu-id="2ca14-351">Perception Simulation Playback</span></span>

<span data-ttu-id="2ca14-352">**/API/Holographic/simulation/playback/file (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="2ca14-353">Supprimer un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-353">Delete a recording.</span></span>

<span data-ttu-id="2ca14-354">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-354">Parameters</span></span>
* <span data-ttu-id="2ca14-355">enregistrement : nom de l’enregistrement à supprimer.</span><span class="sxs-lookup"><span data-stu-id="2ca14-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="2ca14-356">**/API/Holographic/simulation/playback/file (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="2ca14-357">Télécharger un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-357">Upload a recording.</span></span>

<span data-ttu-id="2ca14-358">**/API/Holographic/simulation/playback/Files (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="2ca14-359">Récupération de tous les enregistrements.</span><span class="sxs-lookup"><span data-stu-id="2ca14-359">Get all recordings.</span></span>

<span data-ttu-id="2ca14-360">**/API/Holographic/simulation/playback/session (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="2ca14-361">Obtient l’état de lecture actuel d’un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="2ca14-362">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-362">Parameters</span></span>
* <span data-ttu-id="2ca14-363">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-363">recording : Name of recording.</span></span>

<span data-ttu-id="2ca14-364">**/API/Holographic/simulation/playback/session/file (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="2ca14-365">Décharger un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-365">Unload a recording.</span></span>

<span data-ttu-id="2ca14-366">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-366">Parameters</span></span>
* <span data-ttu-id="2ca14-367">enregistrement : nom de l’enregistrement à décharger.</span><span class="sxs-lookup"><span data-stu-id="2ca14-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="2ca14-368">**/API/Holographic/simulation/playback/session/file (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="2ca14-369">Charger un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-369">Load a recording.</span></span>

<span data-ttu-id="2ca14-370">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-370">Parameters</span></span>
* <span data-ttu-id="2ca14-371">enregistrement : nom de l’enregistrement à charger.</span><span class="sxs-lookup"><span data-stu-id="2ca14-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="2ca14-372">**/API/Holographic/simulation/playback/session/Files (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="2ca14-373">Récupération de tous les enregistrements chargés.</span><span class="sxs-lookup"><span data-stu-id="2ca14-373">Get all loaded recordings.</span></span>

<span data-ttu-id="2ca14-374">**/API/Holographic/simulation/playback/session/pause (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="2ca14-375">Suspendre un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-375">Pause a recording.</span></span>

<span data-ttu-id="2ca14-376">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-376">Parameters</span></span>
* <span data-ttu-id="2ca14-377">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-377">recording : Name of recording.</span></span>

<span data-ttu-id="2ca14-378">**/API/Holographic/simulation/playback/session/Play (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="2ca14-379">Lire un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-379">Play a recording.</span></span>

<span data-ttu-id="2ca14-380">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-380">Parameters</span></span>
* <span data-ttu-id="2ca14-381">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-381">recording : Name of recording.</span></span>

<span data-ttu-id="2ca14-382">**/API/Holographic/simulation/playback/session/Stop (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="2ca14-383">Arrêter un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-383">Stop a recording.</span></span>

<span data-ttu-id="2ca14-384">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-384">Parameters</span></span>
* <span data-ttu-id="2ca14-385">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-385">recording : Name of recording.</span></span>

<span data-ttu-id="2ca14-386">**/API/Holographic/simulation/playback/session/types (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="2ca14-387">Obtenir les types de données dans un enregistrement chargé.</span><span class="sxs-lookup"><span data-stu-id="2ca14-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="2ca14-388">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-388">Parameters</span></span>
* <span data-ttu-id="2ca14-389">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="2ca14-390">Enregistrement de simulation de perception</span><span class="sxs-lookup"><span data-stu-id="2ca14-390">Perception Simulation Recording</span></span>

<span data-ttu-id="2ca14-391">**/API/Holographic/simulation/Recording/Start (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="2ca14-392">Démarrez un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-392">Start a recording.</span></span> <span data-ttu-id="2ca14-393">Un seul enregistrement peut être actif à la fois.</span><span class="sxs-lookup"><span data-stu-id="2ca14-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="2ca14-394">Vous devez définir l’un des principaux, mains, spatialMapping ou environnement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="2ca14-395">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-395">Parameters</span></span>
* <span data-ttu-id="2ca14-396">Head : définissez sur 1 pour enregistrer les données de tête.</span><span class="sxs-lookup"><span data-stu-id="2ca14-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="2ca14-397">mains : définissez sur 1 pour enregistrer les données de la main.</span><span class="sxs-lookup"><span data-stu-id="2ca14-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="2ca14-398">spatialMapping : affectez la valeur 1 pour enregistrer le mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="2ca14-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="2ca14-399">environnement : définissez sur 1 pour enregistrer les données d’environnement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="2ca14-400">nom : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-400">name : Name of the recording.</span></span>
* <span data-ttu-id="2ca14-401">singleSpatialMappingFrame : affectez la valeur 1 pour enregistrer uniquement un seul frame de mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="2ca14-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="2ca14-402">**/API/Holographic/simulation/Recording/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="2ca14-403">Obtient l’état de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="2ca14-403">Get recording state.</span></span>

<span data-ttu-id="2ca14-404">**/API/Holographic/simulation/Recording/Stop (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="2ca14-405">Arrêter l’enregistrement en cours.</span><span class="sxs-lookup"><span data-stu-id="2ca14-405">Stop the current recording.</span></span> <span data-ttu-id="2ca14-406">L’enregistrement est retourné sous la forme d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="2ca14-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="2ca14-407">Données de performances</span><span class="sxs-lookup"><span data-stu-id="2ca14-407">Performance data</span></span>

<span data-ttu-id="2ca14-408">**/API/ResourceManager/Processes (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="2ca14-409">Retourne la liste des processus en cours d’exécution avec les détails</span><span class="sxs-lookup"><span data-stu-id="2ca14-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="2ca14-410">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-410">Return data</span></span>
* <span data-ttu-id="2ca14-411">JSON avec liste de processus et détails pour chaque processus</span><span class="sxs-lookup"><span data-stu-id="2ca14-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="2ca14-412">**/API/ResourceManager/systemperf (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="2ca14-413">Retourne les statistiques de performances système (lecture/écriture d’e/s, statistiques de mémoire, etc.).</span><span class="sxs-lookup"><span data-stu-id="2ca14-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="2ca14-414">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-414">Return data</span></span>
* <span data-ttu-id="2ca14-415">JSON avec informations système : processeur, GPU, mémoire, réseau, e/s</span><span class="sxs-lookup"><span data-stu-id="2ca14-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="2ca14-416">Power</span><span class="sxs-lookup"><span data-stu-id="2ca14-416">Power</span></span>

<span data-ttu-id="2ca14-417">**/API/Power/Battery (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="2ca14-418">Obtient l’état actuel de la batterie</span><span class="sxs-lookup"><span data-stu-id="2ca14-418">Gets the current battery state</span></span>

<span data-ttu-id="2ca14-419">**/API/Power/State (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="2ca14-420">Vérifie si le système est dans un état de faible consommation d’énergie.</span><span class="sxs-lookup"><span data-stu-id="2ca14-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="2ca14-421">Contrôle à distance</span><span class="sxs-lookup"><span data-stu-id="2ca14-421">Remote Control</span></span>

<span data-ttu-id="2ca14-422">**/API/Control/Restart (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="2ca14-423">Redémarre l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="2ca14-423">Restarts the target device</span></span>

<span data-ttu-id="2ca14-424">**/API/Control/Shutdown (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="2ca14-425">Arrête l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="2ca14-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="2ca14-426">Gestionnaire des tâches</span><span class="sxs-lookup"><span data-stu-id="2ca14-426">Task Manager</span></span>

<span data-ttu-id="2ca14-427">**/API/taskmanager/App (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="2ca14-428">Arrête une application moderne</span><span class="sxs-lookup"><span data-stu-id="2ca14-428">Stops a modern app</span></span>

<span data-ttu-id="2ca14-429">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-429">Parameters</span></span>
* <span data-ttu-id="2ca14-430">Package : nom complet du package d’application, hex64 encodé</span><span class="sxs-lookup"><span data-stu-id="2ca14-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="2ca14-431">forceStop : force l’arrêt de tous les processus (= oui)</span><span class="sxs-lookup"><span data-stu-id="2ca14-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="2ca14-432">**/API/taskmanager/App (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="2ca14-433">Démarre une application moderne</span><span class="sxs-lookup"><span data-stu-id="2ca14-433">Starts a modern app</span></span>

<span data-ttu-id="2ca14-434">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-434">Parameters</span></span>
* <span data-ttu-id="2ca14-435">AppID : PRAID de l’application à démarrer, hex64 encodé</span><span class="sxs-lookup"><span data-stu-id="2ca14-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="2ca14-436">Package : nom complet du package d’application, hex64 encodé</span><span class="sxs-lookup"><span data-stu-id="2ca14-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="2ca14-437">Gestion WiFi</span><span class="sxs-lookup"><span data-stu-id="2ca14-437">WiFi Management</span></span>

<span data-ttu-id="2ca14-438">**/API/WiFi/interfaces (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="2ca14-439">Énumère les interfaces de réseau sans fil</span><span class="sxs-lookup"><span data-stu-id="2ca14-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="2ca14-440">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-440">Return data</span></span>
* <span data-ttu-id="2ca14-441">Liste des interfaces sans fil avec des détails (GUID, description, etc.)</span><span class="sxs-lookup"><span data-stu-id="2ca14-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="2ca14-442">**/API/WiFi/Network (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="2ca14-443">Supprime un profil associé à un réseau sur une interface spécifiée</span><span class="sxs-lookup"><span data-stu-id="2ca14-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="2ca14-444">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-444">Parameters</span></span>
* <span data-ttu-id="2ca14-445">Interface : GUID de l’interface réseau</span><span class="sxs-lookup"><span data-stu-id="2ca14-445">interface : network interface guid</span></span>
* <span data-ttu-id="2ca14-446">Profil : nom du profil</span><span class="sxs-lookup"><span data-stu-id="2ca14-446">profile : profile name</span></span>

<span data-ttu-id="2ca14-447">**/API/WiFi/Networks (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="2ca14-448">Énumère les réseaux sans fil sur l’interface réseau spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2ca14-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="2ca14-449">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-449">Parameters</span></span>
* <span data-ttu-id="2ca14-450">Interface : GUID de l’interface réseau</span><span class="sxs-lookup"><span data-stu-id="2ca14-450">interface : network interface guid</span></span>

<span data-ttu-id="2ca14-451">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-451">Return data</span></span>
* <span data-ttu-id="2ca14-452">Liste des réseaux sans fil détectés sur l’interface réseau avec les détails</span><span class="sxs-lookup"><span data-stu-id="2ca14-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="2ca14-453">**/API/WiFi/Network (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="2ca14-454">Se connecte ou se déconnecte à un réseau sur l’interface spécifiée</span><span class="sxs-lookup"><span data-stu-id="2ca14-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="2ca14-455">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-455">Parameters</span></span>
* <span data-ttu-id="2ca14-456">Interface : GUID de l’interface réseau</span><span class="sxs-lookup"><span data-stu-id="2ca14-456">interface : network interface guid</span></span>
* <span data-ttu-id="2ca14-457">SSID : SSID, hex64 encodé, pour se connecter à</span><span class="sxs-lookup"><span data-stu-id="2ca14-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="2ca14-458">opération : se connecter ou se déconnecter</span><span class="sxs-lookup"><span data-stu-id="2ca14-458">op : connect or disconnect</span></span>
* <span data-ttu-id="2ca14-459">CreateProfile : oui ou non</span><span class="sxs-lookup"><span data-stu-id="2ca14-459">createprofile : yes or no</span></span>
* <span data-ttu-id="2ca14-460">clé : clé partagée, encodée en hex64</span><span class="sxs-lookup"><span data-stu-id="2ca14-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="2ca14-461">Enregistreur de performances Windows</span><span class="sxs-lookup"><span data-stu-id="2ca14-461">Windows Performance Recorder</span></span>

<span data-ttu-id="2ca14-462">**/API/WPR/customtrace (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="2ca14-463">Charge un profil WPR et démarre le suivi à l’aide du profil chargé.</span><span class="sxs-lookup"><span data-stu-id="2ca14-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="2ca14-464">Payload</span><span class="sxs-lookup"><span data-stu-id="2ca14-464">Payload</span></span>
* <span data-ttu-id="2ca14-465">corps http en plusieurs parties, conforme</span><span class="sxs-lookup"><span data-stu-id="2ca14-465">multi-part conforming http body</span></span>

<span data-ttu-id="2ca14-466">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-466">Return data</span></span>
* <span data-ttu-id="2ca14-467">Retourne l’état de la session WPR.</span><span class="sxs-lookup"><span data-stu-id="2ca14-467">Returns the WPR session status.</span></span>

<span data-ttu-id="2ca14-468">**/API/WPR/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="2ca14-469">Récupère l’état de la session WPR</span><span class="sxs-lookup"><span data-stu-id="2ca14-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="2ca14-470">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-470">Return data</span></span>
* <span data-ttu-id="2ca14-471">État de session WPR.</span><span class="sxs-lookup"><span data-stu-id="2ca14-471">WPR session status.</span></span>

<span data-ttu-id="2ca14-472">**/API/WPR/trace (récupération)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="2ca14-473">Arrête une session de suivi WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="2ca14-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="2ca14-474">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-474">Return data</span></span>
* <span data-ttu-id="2ca14-475">Retourne le fichier ETL de trace</span><span class="sxs-lookup"><span data-stu-id="2ca14-475">Returns the trace ETL file</span></span>

<span data-ttu-id="2ca14-476">**/API/WPR/trace (publication)**</span><span class="sxs-lookup"><span data-stu-id="2ca14-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="2ca14-477">Démarre une session de suivi WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="2ca14-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="2ca14-478">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ca14-478">Parameters</span></span>
* <span data-ttu-id="2ca14-479">Profil : nom du profil.</span><span class="sxs-lookup"><span data-stu-id="2ca14-479">profile : Profile name.</span></span> <span data-ttu-id="2ca14-480">Les profils disponibles sont stockés dans perfprofiles/profiles.jssur</span><span class="sxs-lookup"><span data-stu-id="2ca14-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="2ca14-481">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="2ca14-481">Return data</span></span>
* <span data-ttu-id="2ca14-482">Dans Démarrer, retourne l’état de la session WPR.</span><span class="sxs-lookup"><span data-stu-id="2ca14-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ca14-483">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ca14-483">See also</span></span>
* [<span data-ttu-id="2ca14-484">Utilisation du portail d’appareil Windows</span><span class="sxs-lookup"><span data-stu-id="2ca14-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="2ca14-485">Informations de référence sur l’API principale du portail des appareils (UWP)</span><span class="sxs-lookup"><span data-stu-id="2ca14-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
