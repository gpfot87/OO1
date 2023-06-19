# OO1
subject one
import argparse

def add_todo(args):
    print("Adding TODO:", args.todo)

def list_todos(args):
    print("Listing all TODOs")

def remove_todo(args):
    print("Removing TODO:", args.todo)

def main():
    parser = argparse.ArgumentParser(description="TODO List Application")
    subparsers = parser.add_subparsers(title="Commands", dest="command")

    # Add command
    add_parser = subparsers.add_parser("add", help="Add a new TODO")
    add_parser.add_argument("todo", type=str, help="TODO description")
    add_parser.set_defaults(func=add_todo)

    # List command
    list_parser = subparsers.add_parser("list", help="List all TODOs")
    list_parser.set_defaults(func=list_todos)

    # Remove command
    remove_parser = subparsers.add_parser("remove", help="Remove a TODO")
    remove_parser.add_argument("todo", type=str, help="TODO description")
    remove_parser.set_defaults(func=remove_todo)

    args = parser.parse_args()

    if hasattr(args, "func"):
        args.func(args)
    else:
        parser.print_help()

if __name__ == "__main__":
    main()

