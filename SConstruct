import os, subprocess, platform, sys

libs_path = [
            'E:\Godot CPP Bindings\lib'
            ]

libs =  [
        'libgodot-cpp.windows.Debug.lib',
        'libgodot-cpp.windows.Release.lib'
        ]

include_path =  [
                "E:\\Godot CPP Bindings\\headers",
                "E:\\Godot CPP Bindings\\include",
                "E:\\Godot CPP Bindings\\include\\core",
                "E:\\Godot CPP Bindings\\include\\gen"
                ]

env = Environment(CPPPATH = include_path)

opts = Variables([],ARGUMENTS)
opts.Add(EnumVariable
            (
                'target','Compilation target', 'release', 
                allowed_values=('debug','release'),
                ignorecase = 2
            )                     
        )

opts.Update(env)

if env['target'] == 'debug':
    env.Append(CCFLAGS = '/W3')
    env.Append(CCFLAGS = '/MDd')
    env.Append(CCFLAGS = '/Zi')
    env.Append(CCFLAGS = '/EHsc')
    env.Append(CCFLAGS = '/D_EBUG')
    env.Append(CCFLAGS = '/FS')

    Mkdir('godot\\native')
    env.SharedLibrary(target='godot\\native\\tost', source=Glob('src\\*.cpp'), INCLUDE = include_path, LIBS = libs[0], LIBPATH = libs_path)
    
else:
    env.Append(CCFLAGS = '/W3')
    env.Append(CCFLAGS = '/MD')
    env.Append(CCFLAGS = '/Zi')
    env.Append(CCFLAGS = '/Ox')
    env.Append(CCFLAGS = '/EHsc')
    env.Append(CCFLAGS = '/DNDEBUG')
    env.Append(CCFLAGS = '/FS')

    Mkdir('godot\\native')
    env.SharedLibrary(target='godot\\native\\test', source=Glob('src\\*.cpp'), INCLUDE = include_path, LIBS = libs[1], LIBPATH = libs_path)




