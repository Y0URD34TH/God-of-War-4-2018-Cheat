	lua[("collectgarbage")] = sol::nil;
	lua[("dofilsse")] = sol::nil;
	lua[("load")] = sol::nil;
	lua[("loadfile")] = sol::nil;
	lua[("pcall")] = sol::nil;
	lua[("print")] = ns_client::log;
	lua[("xpcall")] = sol::nil;
	lua[("getmetatable")] = sol::nil;
	lua[("setmetatable")] = sol::nil;
	lua[("__nil_callback")] = [](){};

	auto client = lua.create_table();
	client[("add_callback")] = ns_client::add_callback;
	client[("load_script")] = ns_client::load_script;
	client[("unload_script")] = ns_client::unload_script;
	client[("log")] = ns_client::log;


	auto menu = lua.create_table();
	menu[("next_line")] = ns_menu::next_line;
	menu[("add_check_box")] = ns_menu::add_check_box;
	menu[("add_combo_box")] = ns_menu::add_combo_box;
	menu[("add_slider_int")] = ns_menu::add_slider_int;
	menu[("add_slider_float")] = ns_menu::add_slider_float;
	menu[("add_color_picker")] = ns_menu::add_color_picker;
	menu[("get_bool")] = ns_menu::get_bool;
	menu[("get_int")] = ns_menu::get_int;
	menu[("get_float")] = ns_menu::get_float;

	auto utils = lua.create_table();//new
	utils[("find_pattern_ida")] = Utils::FindPatternIDA;//new
	utils[("find_pattern_ida64")] = Utils::FindPatternIDA64;//new
	utils[("find_pattern")] = ns_utils::find_signature;//new
	utils[("find_pattern64")] = ns_utils::find_signature64;//new
	utils[("AtachConsole")] = Utils::AttachConsole;//new
	utils[("DetachConsole")] = Utils::DetachConsole;//new
	utils[("ConsolePrint")] = Utils::ConsolePrint;//new

	auto memory = lua.create_table();//new
	memory[("Nop")] = mem::Nop;//new
	memory[("NopEx")] = mem::NopEx;//new
	memory[("Patch")] = mem::Patch;//new
	memory[("PathcEx")] = mem::PatchEx;//new

	auto http = lua.create_table();//new
	http[("get")] = ns_http::get;//new
	http[("post")] = ns_http::post;//new

	auto file = lua.create_table();//new
	file[("append")] = ns_file::append; //new
	file[("write")] = ns_file::write;//new
	file[("read")] = ns_file::read;//new

	auto game = lua.create_table();//new
	game[("player_health")] = g_LocalPlayer->Health;
	game[("player_rage")] = g_LocalPlayer->Rage;//new
	game[("player_maxhealth")] = g_LocalPlayer->MaxHealth();//new
	game[("player_maxrage")] = g_LocalPlayer->MaxRage();//new
	game[("player_basehealth")] = g_LocalPlayer->HealthPtr->BaseMaxHealth;//new
	game[("player_baserage")] = g_LocalPlayer->RagePtr->BaseMaxRage;//new
	game[("player_size")] = g_LocalPlayer->PlayerSize;//new
	game[("player_animspeed")] = g_LocalPlayer->AnimSpeed;//new
	game[("aterus_health")] = g_Atreus->Health;//new
	game[("atreus_arrows")] = g_Atreus->CurrentArrows;//new
	game[("atreus_basemaxhealth")] = g_Atreus->HealthPtr->BaseMaxHealth;//new
	game[("atreus_basemaxarrows")] = g_Atreus->ArrowsPtr->MaxArrows;//new
	game[("player_position")] = g_LocalPlayer->Pos;//new
	game[("atreus_position")] = g_Atreus->Position;//new
	game[("atreus_size")] = g_Atreus->Size;//new
	game[("atreus_animspeed")] = g_Atreus->AnimSpeed;//new
	game[("inventory_hacksilver")] = g_Inventory->HackSilver;//new
	game[("inventory_xp")] = g_Inventory->XP;//new
	game[("inventory_mineralresidue")] = g_Inventory->MineralResidue;//new
	game[("inventory_axereinforcement")] = g_Inventory->AxeReinforcement;//new
	game[("inventory_bladesreinforcement")] = g_Inventory->BladesReinforcement;//new
	game[("inventory_maxrage")] = g_Inventory->MaxRageUpgrade;//new
	game[("inventory_maxhealth")] = g_Inventory->MaxHealthUpgrade;//new
	game[("inventory_reinforcementcommon")] = g_Inventory->ReinforcementCommon;//new
	game[("inventory_reinforcementuncommon")] = g_Inventory->ReinforcementUncommon;//new
	game[("inventory_reinforcementrare")] = g_Inventory->ReinforcementRare;//new
	game[("inventory_talismanreinforcement")] = g_Inventory->TalismanReinforcement;//new
	game[("inventory_brasaardente")] = g_Inventory->BrasaArdente;//new
	game[("camera_position")] = g_Camera->Pos;//to change camera position, nop the address that lock them


	lua[("client")] = client;
	lua[("menu")] = menu;
	lua[("utils")] = utils;//new
	lua[("memory")] = memory;//new
	lua[("http")] = http;//new
	lua[("file")] = file;//new
	lua[("game")] = game;//new
