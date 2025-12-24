I'll analyze the source code to create comprehensive user-facing documentation for project creation and management. Let me start by exploring the project structure.

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" | grep -E "(project|Project)" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="output">
./src/app/(authenticated)/dashboard/project-card.tsx
./src/app/(authenticated)/dashboard/create-project-button.tsx
./src/app/(authenticated)/project/[id]/page.tsx
./src/app/(authenticated)/project/[id]/settings/page.tsx
./src/app/(authenticated)/project/[id]/layout.tsx
./src/components/project-selector.tsx
./src/components/dashboard/project-list.tsx
./src/components/dashboard/create-project-modal.tsx
./src/components/project/project-settings.tsx
./src/components/project/delete-project-dialog.tsx
./src/lib/api/projects.ts
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/dashboard/create-project-modal.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">import { useState } from 'react';
import { Dialog, DialogContent, DialogDescription, DialogFooter, DialogHeader, DialogTitle } from '@/components/ui/dialog';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import { Textarea } from '@/components/ui/textarea';
import { useRouter } from 'next/navigation';
import { createProject } from '@/lib/api/projects';
import { toast } from 'sonner';

interface CreateProjectModalProps {
  open: boolean;
  onOpenChange: (open: boolean) => void;
}

export function CreateProjectModal({ open, onOpenChange }: CreateProjectModalProps) {
  const [name, setName] = useState('');
  const [description, setDescription] = useState('');
  const [isLoading, setIsLoading] = useState(false);
  const router = useRouter();

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    
    if (!name.trim()) {
      toast.error('Please enter a project name');
      return;
    }

    setIsLoading(true);
    try {
      const project = await createProject({ name, description });
      toast.success('Project created successfully');
      onOpenChange(false);
      setName('');
      setDescription('');
      router.push(`/project/${project.id}`);
    } catch (error) {
      toast.error('Failed to create project');
      console.error(error);
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <Dialog open={open} onOpenChange={onOpenChange}>
      <DialogContent className="sm:max-w-[425px]">
        <DialogHeader>
          <DialogTitle>Create New Project</DialogTitle>
          <DialogDescription>
            Give your project a name and description to get started.
          </DialogDescription>
        </DialogHeader>
        <form onSubmit={handleSubmit}>
          <div className="grid gap-4 py-4">
            <div className="grid gap-2">
              <Label htmlFor="name">Project Name</Label>
              <Input
                id="name"
                placeholder="My Awesome Project"
                value={name}
                onChange={(e) => setName(e.target.value)}
                autoFocus
              />
            </div>
            <div className="grid gap-2">
              <Label htmlFor="description">Description (Optional)</Label>
              <Textarea
                id="description"
                placeholder="What's this project about?"
                value={description}
                onChange={(e) => setDescription(e.target.value)}
                rows={3}
              />
            </div>
          </div>
          <DialogFooter>
            <Button type="button" variant="outline" onClick={() => onOpenChange(false)}>
              Cancel
            </Button>
            <Button type="submit" disabled={isLoading}>
              {isLoading ? 'Creating...' : 'Create Project'}
            </Button>
          </DialogFooter>
        </form>
      </DialogContent>
    </Dialog>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/app/(authenticated)/dashboard/create-project-button.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { Button } from '@/components/ui/button';
import { Plus } from 'lucide-react';
import { useState } from 'react';
import { CreateProjectModal } from '@/components/dashboard/create-project-modal';

export function CreateProjectButton() {
  const [open, setOpen] = useState(false);

  return (
    <>
      <Button onClick={() => setOpen(true)} className="gap-2">
        <Plus className="h-4 w-4" />
        New Project
      </Button>
      <CreateProjectModal open={open} onOpenChange={setOpen} />
    </>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/dashboard/project-list.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useEffect, useState } from 'react';
import { getProjects } from '@/lib/api/projects';
import { ProjectCard } from '@/app/(authenticated)/dashboard/project-card';
import { Skeleton } from '@/components/ui/skeleton';
import { Project } from '@/types/project';

export function ProjectList() {
  const [projects, setProjects] = useState<Project[]>([]);
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    const loadProjects = async () => {
      try {
        const data = await getProjects();
        setProjects(data);
      } catch (error) {
        console.error('Failed to load projects:', error);
      } finally {
        setIsLoading(false);
      }
    };

    loadProjects();
  }, []);

  if (isLoading) {
    return (
      <div className="grid gap-4 md:grid-cols-2 lg:grid-cols-3">
        {[...Array(3)].map((_, i) => (
          <Skeleton key={i} className="h-[200px]" />
        ))}
      </div>
    );
  }

  if (projects.length === 0) {
    return (
      <div className="text-center py-12">
        <h3 className="text-lg font-semibold mb-2">No projects yet</h3>
        <p className="text-muted-foreground">
          Create your first project to get started
        </p>
      </div>
    );
  }

  return (
    <div className="grid gap-4 md:grid-cols-2 lg:grid-cols-3">
      {projects.map((project) => (
        <ProjectCard key={project.id} project={project} />
      ))}
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/app/(authenticated)/dashboard/project-card.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';
import { Badge } from '@/components/ui/badge';
import { Project } from '@/types/project';
import { useRouter } from 'next/navigation';
import { formatDistanceToNow } from 'date-fns';
import { FolderOpen } from 'lucide-react';

interface ProjectCardProps {
  project: Project;
}

export function ProjectCard({ project }: ProjectCardProps) {
  const router = useRouter();

  return (
    <Card 
      className="cursor-pointer hover:shadow-lg transition-shadow"
      onClick={() => router.push(`/project/${project.id}`)}
    >
      <CardHeader>
        <div className="flex items-start justify-between">
          <div className="flex items-center gap-2">
            <FolderOpen className="h-5 w-5 text-primary" />
            <CardTitle className="text-xl">{project.name}</CardTitle>
          </div>
          {project.status && (
            <Badge variant={project.status === 'active' ? 'default' : 'secondary'}>
              {project.status}
            </Badge>
          )}
        </div>
        <CardDescription>
          {project.description || 'No description provided'}
        </CardDescription>
      </CardHeader>
      <CardContent>
        <div className="flex justify-between text-sm text-muted-foreground">
          <span>
            Updated {formatDistanceToNow(new Date(project.updated_at), { addSuffix: true })}
          </span>
        </div>
      </CardContent>
    </Card>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/project/project-settings.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useState } from 'react';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import { Textarea } from '@/components/ui/textarea';
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';
import { toast } from 'sonner';
import { updateProject } from '@/lib/api/projects';
import { Project } from '@/types/project';
import { DeleteProjectDialog } from './delete-project-dialog';
import { Separator } from '@/components/ui/separator';

interface ProjectSettingsProps {
  project: Project;
  onUpdate: (project: Project) => void;
}

export function ProjectSettings({ project, onUpdate }: ProjectSettingsProps) {
  const [name, setName] = useState(project.name);
  const [description, setDescription] = useState(project.description || '');
  const [isLoading, setIsLoading] = useState(false);

  const handleSave = async () => {
    if (!name.trim()) {
      toast.error('Project name is required');
      return;
    }

    setIsLoading(true);
    try {
      const updatedProject = await updateProject(project.id, {
        name,
        description,
      });
      toast.success('Project updated successfully');
      onUpdate(updatedProject);
    } catch (error) {
      toast.error('Failed to update project');
      console.error(error);
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <div className="space-y-6">
      <Card>
        <CardHeader>
          <CardTitle>Project Information</CardTitle>
          <CardDescription>
            Update your project's name and description
          </CardDescription>
        </CardHeader>
        <CardContent className="space-y-4">
          <div className="space-y-2">
            <Label htmlFor="project-name">Project Name</Label>
            <Input
              id="project-name"
              value={name}
              onChange={(e) => setName(e.target.value)}
              placeholder="My Awesome Project"
            />
          </div>
          <div className="space-y-2">
            <Label htmlFor="project-description">Description</Label>
            <Textarea
              id="project-description"
              value={description}
              onChange={(e) => setDescription(e.target.value)}
              placeholder="What's this project about?"
              rows={4}
            />
          </div>
          <Button onClick={handleSave} disabled={isLoading}>
            {isLoading ? 'Saving...' : 'Save Changes'}
          </Button>
        </CardContent>
      </Card>

      <Card className="border-destructive">
        <CardHeader>
          <CardTitle className="text-destructive">Danger Zone</CardTitle>
          <CardDescription>
            Irreversible actions that will affect your project
          </CardDescription>
        </CardHeader>
        <CardContent>
          <div className="space-y-4">
            <div>
              <h4 className="font-medium mb-2">Delete Project</h4>
              <p className="text-sm text-muted-foreground mb-4">
                Once you delete a project, there is no going back. This will permanently delete
                the project and all associated data.
              </p>
              <DeleteProjectDialog projectId={project.id} projectName={project.name} />
            </div>
          </div>
        </CardContent>
      </Card>
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/project/delete-project-dialog.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useState } from 'react';
import {
  AlertDialog,
  AlertDialogAction,
  AlertDialogCancel,
  AlertDialogContent,
  AlertDialogDescription,
  AlertDialogFooter,
  AlertDialogHeader,
  AlertDialogTitle,
  AlertDialogTrigger,
} from '@/components/ui/alert-dialog';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import { deleteProject } from '@/lib/api/projects';
import { toast } from 'sonner';
import { useRouter } from 'next/navigation';
import { Trash2 } from 'lucide-react';

interface DeleteProjectDialogProps {
  projectId: string;
  projectName: string;
}

export function DeleteProjectDialog({ projectId, projectName }: DeleteProjectDialogProps) {
  const [confirmText, setConfirmText] = useState('');
  const [isLoading, setIsLoading] = useState(false);
  const router = useRouter();

  const handleDelete = async () => {
    if (confirmText !== projectName) {
      toast.error('Project name does not match');
      return;
    }

    setIsLoading(true);
    try {
      await deleteProject(projectId);
      toast.success('Project deleted successfully');
      router.push('/dashboard');
    } catch (error) {
      toast.error('Failed to delete project');
      console.error(error);
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <AlertDialog>
      <AlertDialogTrigger asChild>
        <Button variant="destructive" className="gap-2">
          <Trash2 className="h-4 w-4" />
          Delete Project
        </Button>
      </AlertDialogTrigger>
      <AlertDialogContent>
        <AlertDialogHeader>
          <AlertDialogTitle>Are you absolutely sure?</AlertDialogTitle>
          <AlertDialogDescription>
            This action cannot be undone. This will permanently delete the project
            and remove all associated data from our servers.
          </AlertDialogDescription>
        </AlertDialogHeader>
        <div className="space-y-2 py-4">
          <Label htmlFor="confirm">
            Type <span className="font-bold">{projectName}</span> to confirm:
          </Label>
          <Input
            id="confirm"
            value={confirmText}
            onChange={(e) => setConfirmText(e.target.value)}
            placeholder={projectName}
          />
        </div>
        <AlertDialogFooter>
          <AlertDialogCancel>Cancel</AlertDialogCancel>
          <AlertDialogAction
            onClick={handleDelete}
            disabled={confirmText !== projectName || isLoading}
            className="bg-destructive text-destructive-foreground hover:bg-destructive/90"
          >
            {isLoading ? 'Deleting...' : 'Delete Project'}
          </AlertDialogAction>
        </AlertDialogFooter>
      </AlertDialogContent>
    </AlertDialog>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/lib/api/projects.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">import { Project, CreateProjectInput, UpdateProjectInput } from '@/types/project';

const API_BASE_URL = process.env.NEXT_PUBLIC_API_URL || '/api';

export async function getProjects(): Promise<Project[]> {
  const response = await fetch(`${API_BASE_URL}/projects`, {
    credentials: 'include',
  });

  if (!response.ok) {
    throw new Error('Failed to fetch projects');
  }

  return response.json();
}

export async function getProject(id: string): Promise<Project> {
  const response = await fetch(`${API_BASE_URL}/projects/${id}`, {
    credentials: 'include',
  });

  if (!response.ok) {
    throw new Error('Failed to fetch project');
  }

  return response.json();
}

export async function createProject(input: CreateProjectInput): Promise<Project> {
  const response = await fetch(`${API_BASE_URL}/projects`, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    credentials: 'include',
    body: JSON.stringify(input),
  });

  if (!response.ok) {
    throw new Error('Failed to create project');
  }

  return response.json();
}

export async function updateProject(id: string, input: UpdateProjectInput): Promise<Project> {
  const response = await fetch(`${API_BASE_URL}/projects/${id}`, {
    method: 'PATCH',
    headers: {
      'Content-Type': 'application/json',
    },
    credentials: 'include',
    body: JSON.stringify(input),
  });

  if (!response.ok) {
    throw new Error('Failed to update project');
  }

  return response.json();
}

export async function deleteProject(id: string): Promise<void> {
  const response = await fetch(`${API_BASE_URL}/projects/${id}`, {
    method: 'DELETE',
    credentials: 'include',
  });

  if (!response.ok) {
    throw new Error('Failed to delete project');
  }
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/types/project.ts</parameter>
</invoke>
</function_calls>
<parameter name="output">export interface Project {
  id: string;
  name: string;
  description: string | null;
  status: 'active' | 'archived' | null;
  created_at: string;
  updated_at: string;
  user_id: string;
}

export interface CreateProjectInput {
  name: string;
  description?: string;
}

export interface UpdateProjectInput {
  name?: string;
  description?: string;
  status?: 'active' | 'archived';
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/app/(authenticated)/project/[id]/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useEffect, useState } from 'react';
import { useParams } from 'next/navigation';
import { getProject } from '@/lib/api/projects';
import { Project } from '@/types/project';
import { Skeleton } from '@/components/ui/skeleton';
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card';

export default function ProjectPage() {
  const params = useParams();
  const [project, setProject] = useState<Project | null>(null);
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    const loadProject = async () => {
      try {
        const data = await getProject(params.id as string);
        setProject(data);
      } catch (error) {
        console.error('Failed to load project:', error);
      } finally {
        setIsLoading(false);
      }
    };

    loadProject();
  }, [params.id]);

  if (isLoading) {
    return (
      <div className="space-y-6">
        <Skeleton className="h-12 w-64" />
        <Skeleton className="h-[200px]" />
      </div>
    );
  }

  if (!project) {
    return (
      <div className="text-center py-12">
        <h3 className="text-lg font-semibold mb-2">Project not found</h3>
        <p className="text-muted-foreground">
          The project you're looking for doesn't exist
        </p>
      </div>
    );
  }

  return (
    <div className="space-y-6">
      <div>
        <h1 className="text-3xl font-bold">{project.name}</h1>
        {project.description && (
          <p className="text-muted-foreground mt-2">{project.description}</p>
        )}
      </div>

      <Card>
        <CardHeader>
          <CardTitle>Project Overview</CardTitle>
          <CardDescription>
            Welcome to your project workspace
          </CardDescription>
        </CardHeader>
        <CardContent>
          <p className="text-muted-foreground">
            This is your project dashboard. From here, you can manage all aspects of your project.
          </p>
        </CardContent>
      </Card>
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/app/(authenticated)/project/[id]/settings/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useEffect, useState } from 'react';
import { useParams } from 'next/navigation';
import { getProject } from '@/lib/api/projects';
import { Project } from '@/types/project';
import { ProjectSettings } from '@/components/project/project-settings';
import { Skeleton } from '@/components/ui/skeleton';

export default function ProjectSettingsPage() {
  const params = useParams();
  const [project, setProject] = useState<Project | null>(null);
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    const loadProject = async () => {
      try {
        const data = await getProject(params.id as string);
        setProject(data);
      } catch (error) {
        console.error('Failed to load project:', error);
      } finally {
        setIsLoading(false);
      }
    };

    loadProject();
  }, [params.id]);

  if (isLoading) {
    return <Skeleton className="h-[400px]" />;
  }

  if (!project) {
    return (
      <div className="text-center py-12">
        <h3 className="text-lg font-semibold mb-2">Project not found</h3>
      </div>
    );
  }

  return (
    <div>
      <div className="mb-6">
        <h1 className="text-3xl font-bold">Project Settings</h1>
        <p className="text-muted-foreground mt-2">
          Manage your project settings and preferences
        </p>
      </div>
      <ProjectSettings project={project} onUpdate={setProject} />
    </div>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/components/project-selector.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">'use client';

import { useState, useEffect } from 'react';
import { Check, ChevronsUpDown, Plus } from 'lucide-react';
import { cn } from '@/lib/utils';
import { Button } from '@/components/ui/button';
import {
  Command,
  CommandEmpty,
  CommandGroup,
  CommandInput,
  CommandItem,
} from '@/components/ui/command';
import {
  Popover,
  PopoverContent,
  PopoverTrigger,
} from '@/components/ui/popover';
import { getProjects } from '@/lib/api/projects';
import { Project } from '@/types/project';
import { useRouter, useParams } from 'next/navigation';
import { CreateProjectModal } from './dashboard/create-project-modal';

export function ProjectSelector() {
  const [open, setOpen] = useState(false);
  const [createModalOpen, setCreateModalOpen] = useState(false);
  const [projects, setProjects] = useState<Project[]>([]);
  const router = useRouter();
  const params = useParams();
  const currentProjectId = params.id as string;

  useEffect(() => {
    const loadProjects = async () => {
      try {
        const data = await getProjects();
        setProjects(data);
      } catch (error) {
        console.error('Failed to load projects:', error);
      }
    };

    loadProjects();
  }, []);

  const currentProject = projects.find((p) => p.id === currentProjectId);

  return (
    <>
      <Popover open={open} onOpenChange={setOpen}>
        <PopoverTrigger asChild>
          <Button
            variant="outline"
            role="combobox"
            aria-expanded={open}
            className="w-[200px] justify-between"
          >
            {currentProject ? currentProject.name : 'Select project...'}
            <ChevronsUpDown className="ml-2 h-4 w-4 shrink-0 opacity-50" />
          </Button>
        </PopoverTrigger>
        <PopoverContent className="w-[200px] p-0">
          <Command>
            <CommandInput placeholder="Search projects..." />
            <CommandEmpty>No project found.</CommandEmpty>
            <CommandGroup>
              {projects.map((project) => (
                <CommandItem
                  key={project.id}
                  value={project.id}
                  onSelect={() => {
                    router.push(`/project/${project.id}`);
                    setOpen(false);
                  }}
                >
                  <Check
                    className={cn(
                      'mr-2 h-4 w-4',
                      currentProjectId === project.id ? 'opacity-100' : 'opacity-0'
                    )}
                  />
                  {project.name}
                </CommandItem>
              ))}
            </CommandGroup>
            <CommandGroup>
              <CommandItem
                onSelect={() => {
                  setOpen(false);
                  setCreateModalOpen(true);
                }}
              >
                <Plus className="mr-2 h-4 w-4" />
                Create New Project
              </CommandItem>
            </CommandGroup>
          </Command>
        </PopoverContent>
      </Popover>
      <CreateProjectModal open={createModalOpen} onOpenChange={setCreateModalOpen} />
    </>
  );
}
</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/app/(authenticated)/project/[id]/layout.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">import { ProjectSelector } from '@/components/project-selector';
import Link from 'next/link';
import { useParams } from 'next/navigation';

export default function ProjectLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <div className="flex flex-col h-full">
      <div className="border-b">
        <div className="flex h-16 items-center px-4 gap-4">
          <ProjectSelector />
          <nav className="flex items-center space-x-4 lg:space-x-6">
            <Link
              href={`/project/${useParams().id}`}
              className="text-sm font-medium transition-colors hover:text-primary"
            >
              Overview
            </Link>
            <Link
              href={`/project/${useParams().id}/settings`}
              className="text-sm font-medium text-muted-foreground transition-colors hover:text-primary"
            >
              Settings
            </Link>
          </nav>
        </div>
      </div>
      <div className="flex-1 space-y-4 p-8 pt-6">
        {children}
      </div>
    </div>
  );
}
</parameter>

Now let me check the dashboard page to understand the full flow:

<function_calls>
<invoke name="execute_command">
<parameter name="command">find ./src/app -name "page.tsx" | grep dashboard</parameter>
</invoke>
</function_calls>
<parameter name="output">./src/app/(authenticated)/dashboard/page.tsx</parameter>

<function_calls>
<invoke name="read_file">
<parameter name="path">./src/app/(authenticated)/dashboard/page.tsx</parameter>
</invoke>
</function_calls>
<parameter name="output">import { CreateProjectButton } from './create-project-button';
import { ProjectList } from '@/components/dashboard/project-list';

export default function DashboardPage() {
  return (
    <div className="space-y-6">
      <div className="flex items-center justify-between">
        <div>
          <h1 className="