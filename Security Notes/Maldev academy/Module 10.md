compile dll manually
	g++ -c <filename.cpp>
	g++ -shared -o <dllname> <filename.o>

to export function from dll
	extern "C" __declspec(dllexport) <return> <fn_name>
