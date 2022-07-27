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
	game[("player_health")] = ns_game::PHealth;
	game[("player_rage")] = ns_game::PRage;//new
	game[("player_maxhealth")] = ns_game::PMHealth;//new
	game[("player_maxrage")] = ns_game::PMRage;//new
	game[("player_basehealth")] = ns_game::PBHealth;//new
	game[("player_baserage")] = ns_game::PBRage;//new
	game[("player_size")] = ns_game::PSize;//new
	game[("player_animspeed")] = ns_game::PAnimSpeed;//new
	game[("aterus_health")] = ns_game::AHealth;//new
	game[("atreus_arrows")] = ns_game::AArrows;//new
	game[("atreus_basemaxhealth")] = ns_game::AMHealth;//new
	game[("atreus_basemaxarrows")] = ns_game::AMArrows;//new
	game[("player_position")] = ns_game::PPos;//new
	game[("atreus_position")] = ns_game::APos;//new
	game[("atreus_size")] = ns_game::ASize;//new
	game[("atreus_animspeed")] = ns_game::AAnimspeed;//new
	game[("inventory_hacksilver")] = ns_game::IHS;//new
	game[("inventory_xp")] = ns_game::IXP;//new
	game[("inventory_mineralresidue")] = ns_game::IMR;//new
	game[("inventory_axereinforcement")] = ns_game::IAR;//new
	game[("inventory_bladesreinforcement")] = ns_game::IBR;//new
	game[("inventory_maxrageupgrade")] = ns_game::IMRU;//new
	game[("inventory_maxhealthupgrade")] = ns_game::IMHU;//new
	game[("inventory_reinforcementcommon")] = ns_game::IRC;//new
	game[("inventory_reinforcementuncommon")] = ns_game::IRU;//new
	game[("inventory_reinforcementrare")] = ns_game::IRR;//new
	game[("inventory_talismanreinforcement")] = ns_game::ITR;//new
	game[("inventory_brasaardente")] = ns_game::IBR;//new
	game[("inventory_leyptralloy")] = ns_game::ILA;//new
	game[("inventory_asgardiansteel")] = ns_game::IAS;//new
	game[("camera_position")] = ns_game::CPOS;//to change camera position, nop the address that lock them


	lua[("client")] = client;
	lua[("menu")] = menu;
	lua[("utils")] = utils;//new
	lua[("memory")] = memory;//new
	lua[("http")] = http;//new
	lua[("file")] = file;//new
	lua[("game")] = game;//new
